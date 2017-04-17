---
title: "Proc&#233;dure&#160;: cr&#233;er un participant de suivi personnalis&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1b612c7e-2381-4a7c-b07a-77030415f2a3
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# Proc&#233;dure&#160;: cr&#233;er un participant de suivi personnalis&#233;
Le suivi de workflow offre une visibilité dans l'état d'exécution de workflow.L'exécution de workflow émet des enregistrements de suivi qui décrivent les événements de cycle de vie du workflow, les événements de cycle de vie de l'activité, la reprise de signet et les erreurs.Ces enregistrements de suivi sont consommés par les participants de suivi.[!INCLUDE[wf](../../../includes/wf-md.md)] inclut un participant de trace standard qui écrit des enregistrements de suivi en tant qu'événements de suivi d'événements pour Windows \(ETW\).Si cela ne répond pas à vos besoins, vous pouvez également écrire un participant de suivi personnalisé.Cette étape du didacticiel décrit comment créer un participant de suivi et un modèle de suivi qui capturent la sortie des activités de `WriteLine` afin qu'elles puissent être affichées à l'utilisateur.  
  
> [!NOTE]
>  Chaque rubrique du didacticiel de mise en route dépend des rubriques précédentes.Pour effectuer cette rubrique, vous devez d'abord terminer les rubriques précédentes.Pour télécharger une version complète ou consulter une procédure pas à pas vidéo du didacticiel, consultez [Windows Workflow Foundation \(WF45\) \- Didacticiel de mise en route](http://go.microsoft.com/fwlink/?LinkID=248976).  
  
## Dans cette rubrique  
  
-   [Pour créer le participant de suivi personnalisé](../../../docs/framework/windows-workflow-foundation//how-to-create-a-custom-tracking-participant.md#BKMK_CustomTrackingParticipant)  
  
-   [Pour créer le modèle de suivi et inscrire le participant de suivi](../../../docs/framework/windows-workflow-foundation//how-to-create-a-custom-tracking-participant.md#BKMK_TrackingProfile)  
  
-   [Pour afficher les informations de suivi](../../../docs/framework/windows-workflow-foundation//how-to-create-a-custom-tracking-participant.md#BKMK_DisplayTracking)  
  
-   [Pour générer et exécuter l'application](../../../docs/framework/windows-workflow-foundation//how-to-create-a-custom-tracking-participant.md#BKMK_BuildAndRun)  
  
###  <a name="BKMK_CustomTrackingParticipant"></a> Pour créer le participant de suivi personnalisé  
  
1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur **NumberGuessWorkflowHost**, puis sélectionnez **Ajouter**, **Classe**.Dans la zone **Nom**, tapez `StatusTrackingParticipant` et cliquez sur **Ajouter**.  
  
2.  Ajoutez les instructions `using` \(ou `Imports`\) suivantes au début du fichier avec les autres instructions `using` \(ou `Imports`\).  
  
    ```vb  
    Imports System.Activities.Tracking  
    Imports System.IO  
    ```  
  
    ```csharp  
    using System.Activities.Tracking;  
    using System.IO;  
    ```  
  
3.  Modifiez la classe `StatusTrackingParticipant` afin qu'elle hérite de `TrackingParticipant`.  
  
    ```vb  
    Public Class StatusTrackingParticipant  
        Inherits TrackingParticipant  
  
    End Class  
    ```  
  
    ```csharp  
    class StatusTrackingParticipant : TrackingParticipant  
    {  
    }  
    ```  
  
4.  Ajoutez la substitution de méthode `Track` suivante.Il existe plusieurs types différents d'enregistrements de suivi.Nous sommes intéressés par la sortie des activités `WriteLine`, qui sont contenues dans les enregistrements de suivi d'activité.Si `TrackingRecord` est un `ActivityTrackingRecord` d'une activité `WriteLine`, la propriété `Text` de l'activité `WriteLine` est ajoutée à un fichier nommé après le `InstanceId` du workflow.Dans ce didacticiel, le fichier est enregistré dans le dossier actif de l'application hôte.  
  
    ```vb  
    Protected Overrides Sub Track(record As TrackingRecord, timeout As TimeSpan)  
        Dim asr As ActivityStateRecord = TryCast(record, ActivityStateRecord)  
  
        If Not asr Is Nothing Then  
            If asr.State = ActivityStates.Executing And _  
            asr.Activity.TypeName = "System.Activities.Statements.WriteLine" Then  
  
                'Append the WriteLine output to the tracking  
                'file for this instance.  
                Using writer As StreamWriter = File.AppendText(record.InstanceId.ToString())  
                    writer.WriteLine(asr.Arguments("Text"))  
                    writer.Close()  
                End Using  
            End If  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    protected override void Track(TrackingRecord record, TimeSpan timeout)  
    {  
        ActivityStateRecord asr = record as ActivityStateRecord;  
  
        if (asr != null)  
        {  
            if (asr.State == ActivityStates.Executing &&  
                asr.Activity.TypeName == "System.Activities.Statements.WriteLine")  
            {  
                // Append the WriteLine output to the tracking  
                // file for this instance  
                using (StreamWriter writer = File.AppendText(record.InstanceId.ToString()))  
                {  
                    writer.WriteLine(asr.Arguments["Text"]);  
                    writer.Close();  
                }  
            }  
        }  
    }  
    ```  
  
     Si aucun modèle de suivi n'est spécifié, le modèle de suivi par défaut est utilisé.Lorsque le modèle de suivi par défaut est utilisé, les enregistrements de suivi sont émis pour tous les `ActivityStates`.Étant donné que nous devons uniquement capturer le texte une seule fois pendant le cycle de vie de l'activité `WriteLine`, nous extrayons uniquement le texte de l'état `ActivityStates.Executing`.Dans [Pour créer le modèle de suivi et inscrire le participant de suivi](../../../docs/framework/windows-workflow-foundation//how-to-create-a-custom-tracking-participant.md#BKMK_TrackingProfile), un modèle de suivi est créé spécifiant que seuls les enregistrements de suivi `WriteLine` `ActivityStates.Executing` sont émis.  
  
###  <a name="BKMK_TrackingProfile"></a> Pour créer le modèle de suivi et inscrire le participant de suivi  
  
1.  Cliquez avec le bouton droit sur **WorkflowHostForm** dans l'**Explorateur de solutions** et sélectionnez **Afficher le code**.  
  
2.  Ajoutez l'instruction `using` \(ou `Imports`\) suivante au début du fichier avec les autres instructions `using` \(ou `Imports`\).  
  
    ```vb  
    Imports System.Activities.Tracking  
    ```  
  
    ```csharp  
    using System.Activities.Tracking;  
    ```  
  
3.  Ajoutez le code suivant à `ConfigureWorkflowApplication` juste après le code qui ajoute `StringWriter` aux extensions de workflow et avant les gestionnaires de cycle de vie de workflow.  
  
    ```vb  
    'Add the custom tracking participant with a tracking profile  
    'that only emits tracking records for WriteLine activities.  
    Dim query As New ActivityStateQuery()  
    query.ActivityName = "WriteLine"  
    query.States.Add(ActivityStates.Executing)  
    query.Arguments.Add("Text")  
  
    Dim profile As New TrackingProfile()  
    profile.Queries.Add(query)  
  
    Dim stp As New StatusTrackingParticipant()  
    stp.TrackingProfile = profile  
  
    wfApp.Extensions.Add(stp)  
    ```  
  
    ```csharp  
    // Add the custom tracking participant with a tracking profile  
    // that only emits tracking records for WriteLine activities.  
    StatusTrackingParticipant stp = new StatusTrackingParticipant  
    {  
        TrackingProfile = new TrackingProfile  
        {  
            Queries =   
            {  
                new ActivityStateQuery  
                {  
                    ActivityName = "WriteLine",  
                    States = { ActivityStates.Executing },  
                    Arguments = { "Text" }  
                }  
            }  
        }  
    };  
  
    wfApp.Extensions.Add(stp);  
    ```  
  
     Ce modèle de suivi spécifie que seuls les enregistrements d'état d'activité des activités `WriteLine` dans l'état `Executing` sont émis au participant de suivi personnalisé.  
  
     Après avoir ajouté le code, le début de `ConfigureWorkflowApplication` sera semblable à l'exemple ci\-dessous.  
  
    ```vb  
    Private Sub ConfigureWorkflowApplication(wfApp As WorkflowApplication)  
        'Configure the persistence store.  
        wfApp.InstanceStore = store  
  
        'Add a StringWriter to the extensions. This captures the output  
        'from the WriteLine activities so we can display it in the form.  
        Dim sw As New StringWriter()  
        wfApp.Extensions.Add(sw)  
  
        'Add the custom tracking participant with a tracking profile  
        'that only emits tracking records for WriteLine activities.  
        Dim query As New ActivityStateQuery()  
        query.ActivityName = "WriteLine"  
        query.States.Add(ActivityStates.Executing)  
        query.Arguments.Add("Text")  
  
        Dim profile As New TrackingProfile()  
        profile.Queries.Add(query)  
  
        Dim stp As New StatusTrackingParticipant()  
        stp.TrackingProfile = profile  
  
        wfApp.Extensions.Add(stp)  
  
        'Workflow lifecycle handlers...  
    ```  
  
    ```csharp  
    private void ConfigureWorkflowApplication(WorkflowApplication wfApp)  
    {  
        // Configure the persistence store.  
        wfApp.InstanceStore = store;  
  
        // Add a StringWriter to the extensions. This captures the output  
        // from the WriteLine activities so we can display it in the form.  
        StringWriter sw = new StringWriter();  
        wfApp.Extensions.Add(sw);  
  
        // Add the custom tracking participant with a tracking profile  
        // that only emits tracking records for WriteLine activities.  
        StatusTrackingParticipant stp = new StatusTrackingParticipant  
        {  
            TrackingProfile = new TrackingProfile  
            {  
                Queries =   
                {  
                    new ActivityStateQuery  
                    {  
                        ActivityName = "WriteLine",  
                        States = { ActivityStates.Executing },  
                        Arguments = { "Text" }  
                    }  
                }  
            }  
        };  
  
        wfApp.Extensions.Add(stp);  
  
        // Workflow lifecycle handlers...  
    ```  
  
###  <a name="BKMK_DisplayTracking"></a> Pour afficher les informations de suivi  
  
1.  Cliquez avec le bouton droit sur **WorkflowHostForm** dans l'**Explorateur de solutions** et sélectionnez **Afficher le code**.  
  
2.  Dans le gestionnaire `InstanceId_SelectedIndexChanged`, ajoutez le code suivant immédiatement après le code qui supprime la fenêtre d'état.  
  
    ```vb  
    'If there is tracking data for this workflow, display it  
    'in the status window.  
    If File.Exists(WorkflowInstanceId.ToString()) Then  
        Dim status As String = File.ReadAllText(WorkflowInstanceId.ToString())  
        UpdateStatus(status)  
    End If  
    ```  
  
    ```csharp  
    // If there is tracking data for this workflow, display it  
    // in the status window.  
    if (File.Exists(WorkflowInstanceId.ToString()))  
    {  
        string status = File.ReadAllText(WorkflowInstanceId.ToString());  
        UpdateStatus(status);  
    }  
    ```  
  
     Lorsqu'un nouveau workflow est sélectionné dans la liste de workflow, les enregistrements de suivi pour ce workflow sont chargés et affichés dans la fenêtre d'état.Cet exemple est le gestionnaire `InstanceId_SelectedIndexChanged` terminé.  
  
    ```vb  
    Private Sub InstanceId_SelectedIndexChanged(sender As Object, e As EventArgs) Handles InstanceId.SelectedIndexChanged  
        If InstanceId.SelectedIndex = -1 Then  
            Return  
        End If  
  
        'Clear the status window.  
        WorkflowStatus.Clear()  
  
        'If there is tracking data for this workflow, display it  
        'in the status window.  
        If File.Exists(WorkflowInstanceId.ToString()) Then  
            Dim status As String = File.ReadAllText(WorkflowInstanceId.ToString())  
            UpdateStatus(status)  
        End If  
  
        'Get the workflow version and display it.  
        'If the workflow is just starting then this info will not  
        'be available in the persistence store so do not try and retrieve it.  
        If Not WorkflowStarting Then  
            Dim instance As WorkflowApplicationInstance = _  
                WorkflowApplication.GetInstance(WorkflowInstanceId, store)  
  
            WorkflowVersion.Text = _  
                WorkflowVersionMap.GetIdentityDescription(instance.DefinitionIdentity)  
  
            'Unload the instance.  
            instance.Abandon()  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    private void InstanceId_SelectedIndexChanged(object sender, EventArgs e)  
    {  
        if (InstanceId.SelectedIndex == -1)  
        {  
            return;  
        }  
  
        // Clear the status window.  
        WorkflowStatus.Clear();  
  
        // If there is tracking data for this workflow, display it  
        // in the status window.  
        if (File.Exists(WorkflowInstanceId.ToString()))  
        {  
            string status = File.ReadAllText(WorkflowInstanceId.ToString());  
            UpdateStatus(status);  
        }  
  
        // Get the workflow version and display it.  
        // If the workflow is just starting then this info will not  
        // be available in the persistence store so do not try and retrieve it.  
        if (!WorkflowStarting)  
        {  
            WorkflowApplicationInstance instance =  
                WorkflowApplication.GetInstance(this.WorkflowInstanceId, store);  
  
            WorkflowVersion.Text =  
                WorkflowVersionMap.GetIdentityDescription(instance.DefinitionIdentity);  
  
            // Unload the instance.  
            instance.Abandon();  
        }  
    }  
  
    ```  
  
###  <a name="BKMK_BuildAndRun"></a> Pour générer et exécuter l'application  
  
1.  Appuyez sur Ctrl\+Maj\+B pour générer l'application.  
  
2.  Appuyez sur Ctrl\+F5 pour démarrer l'application.  
  
3.  Sélectionnez une plage pour le jeu de devinettes et le type de workflow à démarrer, puis cliquez sur **Nouvelle partie**.Entrez une proposition dans la zone **Deviner** et cliquez sur **Aller à** pour soumettre votre proposition.Notez que l'état du workflow est affiché dans la fenêtre d'état.Cette sortie est capturée à partir des activités `WriteLine`.Basculez vers un workflow différent en en sélectionnant un dans la zone de liste déroulante **ID de l'instance de workflow** et notez que l'état du workflow est supprimé.Revenez au workflow précédent et notez que le mode est restauré, semblable à l'exemple suivant.  
  
    > [!NOTE]
    >  Si vous basculez vers un workflow démarré avant activation du suivi, aucun état ne s'affiche.Mais si vous effectuez des propositions supplémentaires, leur état est enregistré, car le suivi est maintenant activé.  
  
 **Please enter a number between 1 and 10**   
**Your guess is too high.**   
**Please enter a number between 1 and 10**    
    > [!NOTE]
    >  Ces informations sont utiles pour déterminer la plage de nombres aléatoires, mais elles ne contiennent aucune information sur les propositions précédemment effectuées.Ces informations sont disponibles dans l'étape suivante, [Procédure : héberger plusieurs versions d'un workflow côte à côte](../../../docs/framework/windows-workflow-foundation//how-to-host-multiple-versions-of-a-workflow-side-by-side.md).  
  
     Notez l'ID d'instance de workflow, et exécutez le jeu jusqu'à son achèvement.  
  
4.  Ouvrez l'Explorateur Windows et accédez au dossier **NumberGuessWorkflowHost\\bin\\debug** \(ou **bin\\release** selon les paramètres du projet\).Notez qu'en plus des fichiers exécutables du projet, il existe des fichiers avec les noms de fichiers GUID.Identifiez celui qui correspond à l'identificateur d'instance du workflow effectué à l'étape précédente et ouvrez\-le dans le Bloc\-notes.Les informations de suivi contiennent des informations semblables à celles qui suivent.  
  
 **Please enter a number between 1 and 10**   
**Your guess is too high.**   
**Please enter a number between 1 and 10**   
**Your guess is too high.**   
**Please enter a number between 1 and 10**      Outre l'absence de propositions de l'utilisateur, les données de suivi ne contiennent pas d'informations sur la proposition finale du workflow.C'est parce que les informations de suivi contiennent uniquement la sortie `WriteLine` du workflow, et le dernier message qui s'affiche est généré à partir du gestionnaire `Completed` après que le workflow est terminé.Dans l'étape suivante du didacticiel, [Procédure : héberger plusieurs versions d'un workflow côte à côte](../../../docs/framework/windows-workflow-foundation//how-to-host-multiple-versions-of-a-workflow-side-by-side.md), les activités `WriteLine` existantes sont modifiées pour afficher les propositions de l'utilisateur, et une activité `WriteLine` supplémentaire est ajoutée et affiche les résultats finaux.Une fois ces modifications intégrées, [Procédure : héberger plusieurs versions d'un workflow côte à côte](../../../docs/framework/windows-workflow-foundation//how-to-host-multiple-versions-of-a-workflow-side-by-side.md) explique comment héberger plusieurs versions de workflow en même temps.
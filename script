    using System.Collections;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    using UnityEngine.UI;
     
    public class discord : MonoBehaviour
    {
        public string Message;
        public string Subject;
        public GameObject message;
        public GameObject subject;
        string webhook_link = "https://discord.com/api/webhooks/861243170485829643/BJ9aTLeff7oAhxMGpye1lGn6ZHnL_id7R6yr5cfhe2kBSsvzJsw_k26xzbVrS5rF2l2B";
     
        public void Store()
        {
            Message = message.GetComponent<Text>().text;
            Subject = subject.GetComponent<Text>().text;
        }
     
        public void Msg()
        {
            StartCoroutine(SendWebhook(webhook_link, Subject + "     " + Message, (success) =>
            {
                if (success)
                    Debug.Log("good");
            }));
        }
     
        IEnumerator SendWebhook(string link, string message, System.Action<bool> action)
        {
            WWWForm form = new WWWForm();
            form.AddField("content", message);
            using (UnityWebRequest www = UnityWebRequest.Post(link, form))
            {
                yield return www.SendWebRequest();
     
                if (www.isNetworkError || www.isHttpError)
                {
                    Debug.Log(www.error);
                    action(false);
                }
                else
                    action(true);
            }
        }
     
    }
                
                        

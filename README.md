# Build chatbot with  Azure Bot Service

In this workshop, you will learn how :
 * we use a language service
 * by using language resorce create a bot
 * Integrate with Azure Bot Service
 * Chat with the bot to verify the code is working
 * Add Chit-chat personality at your knowledge base
  
## Pre-requisites

* Azure Pass or subscription - [Try it for Free](https://azure.microsoft.com/en-gb/)

## Case description

A bot is an autonomous program that interacts with people or computer systems in a predictable way. The logic behind a bot is designed and programmed by the bot creator, often with the help of tools like the Microsoft Bot Framework. Microsoft also has other AI services, included in Azure Cognitive Services, that can enhance the capabilities of your bots.

## create a language service in azure portal

### by using language service create a bot
![Screenshot 2022-10-08 161103](https://user-images.githubusercontent.com/111121880/194703511-58fa1b53-bfd4-4d5a-8e3a-de201d02f6c4.png)

![image](https://user-images.githubusercontent.com/111121880/194703605-1809de72-e132-4e41-8237-4a202b64bb7a.png)




1. Provide the required information:

**Name:** chatbot-<your initials>
  
**Subscription:** Select your existing subscription

**Pricing tier:** Select F0 (3 Calls per second)

**Resource group:** Clic on Create new and type the name qna-lab-rg

**Resource group location:** Select Canada Central

**Search pricing tier:** Select F (3 Indexes)

**Search Location:** Select Canada Central

**App name:** chatbot-<your initials>
  
**Website Location:** Select Canada Central

**Application Insights Location:** Select Canada Central

   ![image](https://user-images.githubusercontent.com/111121880/194703849-712b6716-59ca-4711-b93a-dc4b8cbff717.png)


1. Click Create to deploy the service. This step might take a few moments.
  ![deploy knowledge base](https://user-images.githubusercontent.com/111121880/194706199-77c05479-7991-438f-9f85-a867e9b54e78.png)

1. select manage services
![manage service in chattbot](https://user-images.githubusercontent.com/111121880/194705544-d6094618-b952-486c-a1da-3c255299f4ef.png)
2. edit knowledge base
![knowledge base](https://user-images.githubusercontent.com/111121880/194705600-3fafc476-89c1-46cb-9060-f7364fc99701.png)
3.deploy knowledge base
![deploy knowledge base](https://user-images.githubusercontent.com/111121880/194705667-86fbdf99-8e9b-4912-ac64-7da38ad9273e.png)
4.create a web app bot
![web app bot](https://user-images.githubusercontent.com/111121880/194705810-32a8e0fa-5437-47c2-93e4-01ca5b286187.png)




Don't close this **Publish** page. You need it later in the tutorial, to create a bot. 

### Use cURL to query for an FAQ answer


1. Run the cURL command and receive the JSON response, including the score and answer. 

    ```TXT
      % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                     Dload  Upload   Total   Spent    Left  Speed
    100   581  100   543  100    38    418     29  0:00:01  0:00:01 --:--:--   447{
      "answers": [
        {
          "questions": [
            "How large a knowledge base can I create?"
          ],
          "answer": "The size of the knowledge base depends on the SKU of Azure search you choose when creating the QnA Maker service. Read [here](https://docs.microsoft.com/azure/cognitive-services/qnamaker/tutorials/choosing-capacity-qnamaker-deployment)for more details.",
          "score": 35.92,
          "id": 2,
          "source": "https://docs.microsoft.com/azure/cognitive-services/qnamaker/faqs",
          "metadata": []
        }
      ]
    }
    
    ```

    QnA Maker is somewhat confident with the score of 35.92%.  


### Use cURL to query for the default answer

Any question that QnA Maker is not confident about receives the default answer. This answer is configured in the Azure portal. 

1. In the cURL-enabled terminal, replace `How large can my KB be?` with `x`. 

1. Run the cURL command and receive the JSON response, including the score and answer. 

    ```TXT
      % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                     Dload  Upload   Total   Spent    Left  Speed
    100   186  100   170  100    16    272     25 --:--:-- --:--:-- --:--:--   297{
      "answers": [
        {
          "questions": [],
          "answer": "No good match found in KB.",
          "score": 0.0,
          "id": -1,
          "metadata": []
        }
      ]
    }
    ```
    

    

##Create a language service Bot with Azure Bot Service v4

### Create a language service Bot

Create a bot as a client application for the knowledge base. 

1. In the QnA Maker portal, go to the **Publish** page, and publish your knowledge base. Select **Create Bot**. 

   


    The Azure portal opens with the bot creation configuration.
![Create the knowledge base bot with these settings.](/media/create-bot-from-azure-portal.PNG)

    Wait a couple of minutes until the bot creation process notification reports success.

<a name="test-the-bot"></a>

### Chat with the Bot

![Screenshot 2022-10-08 163127 chat with bot](https://user-images.githubusercontent.com/111121880/194706337-cb1b2de5-2539-4373-bc4f-db09f0d775c1.png)



### Add personnality with Chit-Chat 

Adding chit-chat to your bot makes it more conversational and engaging. The chit-chat feature in QnA maker allows you to easily add a pre-populated set of the top chit-chat, into your knowledge base (KB). This can be a starting point for your bot's personality, and it will save you the time and cost of writing them from scratch.

This dataset has about 100 scenarios of chit-chat in the voice of multiple personas, like Professional,Friendly and Witty.

Some examples of the different personalities are below. You can see all the personality [datasets](https://github.com/Microsoft/BotBuilder-PersonalityChat/tree/master/CSharp/Datasets) along with details of the personalities.

For the user query of `When is your birthday?`, each personality has a styled response:

<!-- added quotes so acrolinx doesn't score these sentences -->
|Personality|Example|
|--|--|
|Professional|Age doesn't really apply to me.|
|Friendly|I don't really have an age.|
|Witty|I'm age-free.|
|Caring|I don't have an age.|
|Enthusiastic|I'm a bot, so I don't have an age.|
||

#### Add Chit-Chat in your KB

1. Download the English friendly [datasets on GitHub](https://github.com/Microsoft/BotBuilder-PersonalityChat/tree/master/CSharp/Datasets)

1. Go to qnamaker.ai portal. Select your KB and select **Settings** from the top menu.

1. Scroll down to **Manage knowledge base**

1. On **File name** sub section, click on **Add file** and add qna_chitchat_friendly.tsv file.



1. Click **Save and Train** from top menu.

1. Click on **Edit** for review the questions and answers.

1. Select the last page of questions and answers from the bottom of the table. The page shows questions and answers from the Chit-chat personality.

1. From the toolbar above the list of questions and answers, select the View options icon, and then select Show metadata. This shows the metadata tags for each question and answer. The Chit-chat questions have the editorial: chit-chat metadata already set. This metadata is returned to the client application, along with the selected answer. The client application, such as a chat bot, can use this filtered metadata to determine additional processing or interactions with the user.

 



#### Use cURL to query for a Chit-chat answer

1. In the cURL-enabled terminal, replace `How large can my KB be?` with a bot conversation-ending statement from the user, such as `Thank you`.   

1. Run the cURL command and receive the JSON response, including the score and answer. 

    ```TXT
      % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                     Dload  Upload   Total   Spent    Left  Speed
    100   525  100   501  100    24    525     25 --:--:-- --:--:-- --:--:--   550{
      "answers": [
        {
          "questions": [
            "Thank you",
            "Thanks",
            "Thnx",
            "Kthx",
            "I appreciate it",
            "Thank you so much",
            "I thank you",
            "My sincere thank"
          ],
          "answer": "You're very welcome.",
          "score": 100.0,
          "id": 109,
          "source": "qna_chitchat_the_friend.tsv",
          "metadata": [
            {
              "name": "editorial",
              "value": "chitchat"
            }
          ]
        }
      ]
    }
   
    ```

   

#### Chat with the bot

Go back in **Test in Web Chat** on Azure Portal and chat with your bot.

![Screenshot 2022-10-08 163127 chat with bot](https://user-images.githubusercontent.com/111121880/194704243-6369cc8f-c170-4cf1-8a6b-eb1972e178df.png)


## Clean up resources
Finally, If you don't expect to need these resources in the future, you can delete them by deleting the resource group. To do so, select the resource group for this workshop, select Delete, then confirm the name of the resource group to delete.

---
title: Create a Cloud PBX call queue
ms.assetid: 67ccda94-1210-43fb-a25b-7b9785f8a061
---



# Create a Cloud PBX call queue

Skype for Business Online Cloud PBX Call Queues include greetings that are used when someone calls into a phone number for your organization, the ability to automatically put the calls on hold and search for the next available call agent to handle the call while the people who call are listening to music on hold. You can create a single or multiple call queues for your organization.
  
    
    

Cloud PBX Call Queues can provide:
- An organizational greeting.
    
  
- Music while people are waiting on hold.
    
  
- Redirecting calls to call agents in mail-enabled distribution lists and security groups.
    
  
- Making settings for call queue maximum size, timeout and call handling options.
    
  
When someone calls in to a phone number that is setup up with a call queue, they will hear a greeting first (if any is setup), and then they will be put in the queue and wait for the next available call agent. The person calling in will hear music while they are on hold waiting, and the calls will be offered to the call agents in the  *First In, First Out*  (FIFO) manner.All calls waiting in the queue will be distributed using an attendant routing mode:
- The first call in the queue will ring all call agents at the same time.
    
    > [!NOTE]
      > Call agents who are **Offline** or have set their presence to ** Do not Disturb** won't be called.
- Only one incoming call notification (for the call at the head of the queue) at a time will be sent to the call agents.
    
  
- After a call agent accepts the call, the next incoming call in the queue will start ringing call agents.
    
  

## Step 1 - Getting started

To get started using call queues, it's important to remember a few things:
  
    
    

- Your organization must have (at a minimum) an Enterprise E3 plus Skype for Business Cloud PBX license or an Enterprise E5 license. The number of Skype for Business Cloud PBX user licenses that are assigned impacts the number of service numbers that are available to be used for call queues. The number of call queues you can have is dependent on the number Skype for Business Cloud PBX and PSTN Conferencing licenses that are assigned in your organization. To learn more about licensing, go  [Skype for Business add-on licensing](skype-for-business-add-on-licensing.md).
    
    > [!NOTE]
      > To redirect calls to people in your organization that are Online, they must have a Cloud PBX license and be enabled for Enterprise Voice or have PSTN calling plan. See  [Assign Skype for Business licenses](assign-skype-for-business-licenses.md). To enable them for Enterprise Voice, you can use Windows PowerShell. For example run:  `Set-CsUser -identity "Amos Marble" -EnterpriseVoiceEnabled $true`
- To learn more about PSTN Calling, see  [What is PSTN calling?](what-is-pstn-calling.md) and [PSTN Calling plans for Skype for Business](pstn-calling-plans-for-skype-for-business.md)
    
    > [!NOTE]
      > Users hosted on-premises using Skype for Business Server 2015 or Lync Server 2013 and 2010 aren't supported as a Call Queue Agents. 
- You can only assign a toll and toll-free service phone number that you got in the Skype for Business admin center or transferred from another service provider to Cloud PBX Call Queues. To get and use toll-free service numbers, you need to set up PSTN Consumption Billing. To do this, see  [What is PSTN Consumption billing?](what-is-pstn-consumption-billing.md) and [Set up PSTN Consumption billing](set-up-pstn-consumption-billing.md).
    
    > [!NOTE]
      > User (subscriber) phone numbers can't be assigned to call queues - only service toll or toll-free phone numbers can be used. 

- When you are distributing the incoming calls from a Cloud PBX Call Queue, these clients are supported for call agents:
    
  - Skype for Business desktop client 2016 (32 and 64-bit versions)
    
  
  - Lync desktop client 2013 (32 and 64-bit versions)
    
  
  - All IP phone models supported for Skype for Business Online. See,  [Getting phones for Skype for Business Online](getting-phones-for-skype-for-business-online.md). In order to receive call queue calls on IP phones, agents must sign in directly on their phones. 
    
    > [!NOTE]
      >  Call queue agents using mobile apps and Macs aren't supported.

## Step 2 - Getting or transferring toll or toll-free service phone numbers

Before you can create and set up your call queues, you will need to get or transfer your existing toll or toll-free service numbers. Once you get the toll or toll-free service phone numbers, they will show up in the ** Skype for Business admin center** > **Voice** > **Phone numbers** tab and the **Number type** listed will be listed as **Service - Toll-Free**. To get your service numbers, see  [Getting Skype for Business service phone numbers](getting-skype-for-business-service-phone-numbers.md) or if you want to transfer and existing service number, see [Transfer phone numbers to Skype for Business Online](transfer-phone-numbers-to-skype-for-business-online.md).
  
    
    

> [!NOTE]
> If you are outside the U.S., you can't use the Skype for Business admin center to get service numbers. Go  [Get phone numbers for Skype for Business Online](get-phone-numbers-for-skype-for-business-online.md) instead to see how to do it from the outside of the U.S.
  
    
    


## Step 3 - Create a new Call Queue

In the **Skype for Business admin center**, click **Call routing** > **Call queues**, then click **Add new**:
  
    
    

### Set the call queue display name, phone number and domain (if any)


  
    
    
![Setting up a call queue.](images/37ecc300-a108-4294-8463-fce570dfce72.png)
  
    
    

  
    
    

|||
|:-----|:-----|
|**1** <br/> |**Name** Enter a descriptive display name for the call queue. This is required and can contain up to 64 characters, including spaces. <br/> This name will be displayed in the notification for the incoming call.  <br/> |
|**2** <br/> |**Phone number** Select a service toll or toll-free phone number for the call queue. This is required. <br/> If there aren't any listed, you need to get service numbers before you can create this call queue. To get your service numbers, see  [Getting Skype for Business service phone numbers](getting-skype-for-business-service-phone-numbers.md) <br/> |
|**3** <br/> |**Domain** If this is available, choose the Office 365 domain you want to use. This is only available if you have more than one domain being used with Office 365. If you have more than one, you must chose the domain name from the list. <br/> For example, you could have a domain like:  _contoso.com or redmond.contoso.com_ <br/> |
   

### Set the greeting and music played while on hold


  
    
    

  
    
    
![Setting up a call queue.](images/1d395a93-7cab-4178-9295-12d5379e20de.png)
  
    
    

  
    
    

|||
|:-----|:-----|
|**1** <br/> |**Greeting** is optional. This is the greeting that is played for people that call into the call queue number. <br/> You can upload an audio file (.wav, .mp3 or .wma formats).  <br/> |
|**2** <br/> |**Music on hold**, You can either use the default Music on Hold provided with the Call Queue, or you can upload an audio file in .wav, mp3 or .wma formats to use as your custom Music on Hold.  <br/> |
   

### Add call agents to a call queue


  
    
    

  
    
    
![Set up call queues.](images/9c0c551b-218b-4268-9b73-c85000c99296.png)
  
    
    

  
    
    

|||
|:-----|:-----|
|**1**| Call agents (50 maximum) can be: An Online user with a Skype for Business Cloud PBX license and be enabled for Enterprise Voice or have PSTN calling plan.> [!NOTE]>  To redirect calls to people in your organization that are Online, they must have a Cloud PBX license and be enabled for Enterprise Voice or have PSTN calling plan. See [Assign Skype for Business licenses](assign-skype-for-business-licenses.md). To enable them for Enterprise Voice, you can use Windows PowerShell. For example run:  `Set-CsUser -identity "Amos Marble" -EnterpriseVoiceEnabled $true`           Online users with a with a Skype for Business Cloud PBX license or PSTN calling plan that are added to a mail-enabled Distribution List or Security Group. It might take up to 30 minutes for a new agent added for a distribution list or a security group to start receiving calls from a call queue. A newly created distribution list or security group might take up to 48 hours to become available to be used with call queues.> [!NOTE]>  Office 365 Groups (Modern Groups) can't be used with call queues.          > [!NOTE]>  Users hosted on-premises using Skype for Business Server 2015 or Lync Server 2013 and 2010 aren't supported.          |
   

### Set the maximum queue size and maximum wait time


  
    
    

  
    
    
![Set up a call queue.](images/3f018734-16fe-458b-827d-71fc25155cde.png)
  
    
    

  
    
    

|||
|:-----|:-----|
|**1** <br/> |**Maximum calls in the queue** Use this to set the maximum calls that can wait in the queue at the same time. The default is 50 but it can range from 0 to 200. <br/> When this limit is reached, the call will be handled in way you have set on the **When the maximum number of calls is reached** setting below. <br/> |
|**2** <br/> |**When the maximum number of calls is reached** When the call queue reaches it's maximum size (set using the **Maximum calls in the queue** setting), you can choose what happens to new incoming calls. <br/> **Disconnect with a busy signal** The call will be disconnected. <br/> **Forward to** When you choose this, you will have these options: <br/> **Person in your company** An Online user with a Skype for Business Cloud PBX license and be enabled for Enterprise Voice or have PSTN calling plan. You can set it up so the person calling in can be sent to voicemail. To do this, select a **Person in your company** and this person will have their calls forwarded directly to voicemail. <br/> > [!NOTE]>  Users hosted on-premises using Skype for Business Server 2015 and Lync Server 2013 and 2010 aren't supported.          **Call Queue** You must have already created another call queue but after you do, then you can select that call queue. <br/> **Auto Attendant** You must have already created an auto attendant, but after you do, then you can select that auto attendant. See [Set up a Cloud PBX auto attendant](set-up-a-cloud-pbx-auto-attendant.md).  <br/> |
|**3** <br/> |**How long a call can wait in the queue** You can also decide how much time a call can be on hold in the queue before it times out and needs to be redirected or disconnected. Where it will be redirected is based on how you set the **When a call times out** setting. You can set a time from 0 to 45 minutes. <br/> |
|**4** <br/> |**When a call times out** When the call reaches the limit you set on the **How long a call can wait in the queue** setting, you can choose what happens to this call: <br/> **Disconnect** The call will be disconnected. <br/> **Forward to** When you choose this, you will have these options: <br/> **Person in your company** An Online user with a Skype for Business Cloud PBX license and be enabled for Enterprise Voice or have PSTN calling plan. You can set it up so the person calling in can be sent to voicemail. To do this, select a **Person in your company** and this person will have their calls forwarded directly to voicemail. <br/> > [!NOTE]>  Users hosted on-premises using Skype for Business Server 2015 and Lync Server 2013 and 2010 aren't supported.          **Call Queue** You must have already created another call queue, but after you do, then you can select that call queue. <br/> **Auto Attendant** You must have already created an auto attendant, but after you do, then you can select that auto attendant. See, [Set up a Cloud PBX auto attendant](set-up-a-cloud-pbx-auto-attendant.md).  <br/> |
   

## Want to know more?

You can also use Windows PowerShell to create and set up call queues.
  
    
    

### Call queue cmdlets

Here are the cmdlets that you need to manage a call queue.
  
    
    

-  [New-CsHuntgroup](https://technet.microsoft.com/en-us/library/mt796459.aspx)
    
  
-  [Set-CsHuntgroup](https://technet.microsoft.com/en-us/library/mt796457.aspx)
    
  
-  [Get-CsHuntgroup](https://technet.microsoft.com/en-us/library/mt796458.aspx)
    
  
-  [Remove-CsHuntgroup](https://technet.microsoft.com/en-us/library/mt796456.aspx)
    
  

### More about Windows PowerShell


- When it comes to Windows PowerShell is all about managing users and what users are allowed or not allowed to do. With Windows PowerShell, you can manage Office 365 and Skype for Business Online using a single point of administration that can simplify your daily work, when you have multiple tasks to do. To get started with Windows PowerShell, see these topics:
    
  -  [An introduction to Windows PowerShell and Skype for Business Online](https://go.microsoft.com/fwlink/?LinkId=525039)
    
  
  -  [Six Reasons Why You Might Want to Use Windows PowerShell to Manage Office 365 ](https://go.microsoft.com/fwlink/?LinkId=525041)
    
  
- Windows PowerShell has many advantages in speed, simplicity, and productivity over only using the Office 365 admin center such as when you are making setting changes for many users at one time. Learn about these advantages in the following topics:
    
  -  [Best ways to manage Office 365 with Windows PowerShell](https://go.microsoft.com/fwlink/?LinkId=525142)
    
  
  -  [Using Windows PowerShell to manage Skype for Business Online](https://go.microsoft.com/fwlink/?LinkId=525453)
    
  
  -  [Using Windows PowerShell to do common Skype for Business Online management tasks](https://go.microsoft.com/fwlink/?LinkId=525038)
    
  
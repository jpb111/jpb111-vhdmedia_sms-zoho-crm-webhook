# vhdmedia_sms-zoho-crm-webhook
Connecting VHD-media sms platform with zoho CRM webhook

## *Set Up Webhooks for VHDmedia sms in ZohoCRM*
Setting up Webhooks in Zoho CRM includes the following three steps:

1. Create a connection
2. Create a webhook.
2. Associate webhook to a workflow rule.
3. Test webhook integration.

## *To create a connection*

1. In Zoho CRM Go to Setup > Developer Space > Connections> Create Connection.
2. Click create connection page > Custom services > Create New Service
3. In service details page enter a Service name and Service link name of your choice. 
4. Authentication Type > Basic Authentication 
5. Click Create Service
6. Enter Connection name and Connection link name of your choice 
7. Click Create and Connect 
8. There will be a new page open enter the given VHD sms account username and password and click connect. 
9. This will create a connection and you will get a message connection created sucessfully. 


## *To create a webhook to send sms*


1. Go to Setup > Automation > Actions > Webhooks.
2. n the Webhooks page, click Configure Webhook.
3. Give a name and description for the webhook. 
4. Choose Method as POST
5. Enter the VHDMEDIA given api URI to notify 

for example 

```URI

https://example.com/sms/1/text/single

```
6. Authorization Type > Connection 
7. Choose Connection > choose the connection you created before from the dropdown. 
8. Body Type > RAW 
9. Format > JSON
10. Type 

```Json

{
    "to" : "{{${Contacts.Mobile}}}",
    "text" : "Hello ${Contacts.First Name} this is a sample message from VHD media zoho crm"
}


```

In the "to" : key we always needed to enter the filed  where we are entering the mobile number. Suppose we are entering mobile number in the field Phone to select that field enter #,  eg "to" : "{{#}}" and pick the filed from the drop down. 

In similarway to customize the sms text we can use # to pick the field we wanted. 

for eg "text" : "Hello # ", we can pick Contacts.Last Name from the drop down list when we click #. 

![text-body](/images/text-body.png)


## *Create workflow rules* 

Follow the [article Configuring Workflow Rules](https://help.zoho.com/portal/en/kb/crm/automate-business-processes/workflow-management/articles/configuring-workflow-rules#Part_1_-_Enter_the_basic_details_of_the_rule) to create workflow rule. 

Once the rule is created attached our webhook to the rule to send sms when the rule is triggered. 
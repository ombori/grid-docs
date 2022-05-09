# Digital call with Bambuser

Bambuser solution helps you to connect your ecom system and engage customers through the online calls. Queue manager solution from Ombori provides you a way to organize the flow for your staff members in store and between stores.

## Bambuser system provides
Online calls with personal support, leading to increasing your online sales 

## Queue system provides
1. Notifications for incoming calls
2. Auto rotation if the call wasn't picked up but the specified person
3. Calls rotation on different levels - between store managers, different stores / entities and the company level
4. Collecting information about required help and routing of the call to the person / entity which has the specified expertise
5. Analytics of different metrics for the calls (not answered calls, who was answering, call level, etc.)
 
## Configuring
For the using Queue Management system with Bambuser you need to have integration information from Bambuser. Please check the list below:

1. Agent base url - a page to open a call for agents. Received from Bambuser
2. Api token - a token to make API calls. Received from Bambuser
3. Customer url template - Url which redirects customer to call page. Received from Bambuser, depends on your ecom
4. Routing timeout - optional parameter, which determines interval time for searching next available agents if there are no response
5. Digital call queue type - Default or Global - for single queue/store it should be Default. When we have a queue responsible for calling multiple queues/stores, we should select Global
6. Global queue ID - when it’s Default digital call queue type, and you want to have your queue connected to global digital call queue, then you should type id of global queue here

## Apigee-free-book

![Alt Text](https://nordicapis.com/wp-content/uploads/Apigee_TransparentPrimaryLogo-4.png )


Apigee is a platform for developing and managing APIs. By fronting services with a proxy layer, Apigee provides an abstraction or facade for your backend service APIs and provides security, rate limiting, quotas, analytics, and more.

- https://cloud.google.com/apigee/docs/api-platform/get-started/what-apigee



- https://docs.apigee.com
- https://www.youtube.com/playlist?list=PLIXjuPlujxxxe3iTmLtgfIBgpMo7iD7fk
- https://www.youtube.com/playlist?list=PLIXjuPlujxxxe3iTmLtgfIBgpMo7iD7fk
- https://github.com/apigee/openbank
- https://github.com/apigee/api-platform-samples
- https://github.com/swilliams11/apigee-edge-dev-training-accelerated
- https://github.com/apigee/DevJam
- https://github.com/vaquarkhan/Iloveapis-apijam
- https://github.com/apigee/streetcarts-tutorial/tree/master/streetcarts
- https://github.com/apigee/api-platform-samples
- https://github.com/dzuluaga/apigee-tutorials/tree/master/apiproxies
- https://github.com/apigee/DevJam/tree/master/Lab%20Guides/Lab%201%20-%20Design%20and%20Build%20a%20simple%20API%20Proxy
- https://github.com/linuxacademy/content-apigee-api-engineer-exam
- https://github.com/apigee/api-platform-samples/tree/master/doc-samples/java-cookbook
- https://github.com.cnpmjs.org/topics/apigee-edge
- https://github.com/apigee/insights-samples

## Apigee Security  :

API Security focuses on strategies and solutions to understand and mitigate the unique vulnerabilities and security risks of Application Programming Interfaces (APIs).

- https://owasp.org/www-project-api-security/
- https://docs.apigee.com/api-platform/faq/owasp-protection

#### Content-Based Attacks

Content-based API attacks use malformed API requests to cause issues with APIs and backend services. Some attacks use text fields to compromise data in the backend, either retrieving data that the user should not be permitted to get, or destroying data in backend databases.

#### Json threat protection policy - https://docs.apigee.com/api-platform/reference/policies/json-threat-protection-policy


          <JSONThreatProtection async="false" continueOnError="false" enabled="true" name="JTP-Protect">
              <ArrayElementCount>3</ArrayElementCount>
              <ContainerDepth>2</ContainerDepth>
              <ObjectEntryCount>5</ObjectEntryCount>
              <ObjectEntryNameLength>10</ObjectEntryNameLength>
              <Source>request</Source>
              <StringValueLength>20</StringValueLength>
         </JSONThreatProtection>
         
 #### RegularExpressionThreatProtection policy - https://docs.apigee.com/api-platform/reference/policies/regular-expression-protection
 
       <RegularExpressionProtection async="false" continueOnError="false" enabled="true" name="REP-SQLInjection">
          <IgnoreUnresolvedVariables>false</IgnoreUnresolvedVariables>
             <QueryParam name="query">
                  <Pattern>[\s]*(?i)((delete)|(exec)|(drop\s*table)|(insert)|(shutdown)|(update)|(\bor\b))</Pattern>
            </QueryParam>
         <Source>request</Source>
       </RegularExpressionProtection>


- https://docs.oracle.com/javase/tutorial/essential/regex/
 
####  Transport Layer Security, or TLS,

One way vs two way TLS :
implementing one-way SSL authentication, the server application shares its public certificate with the client. In two-way SSL authentication, the client application verifies the identity of the server application, and then the server application verifies the identity of the client application.



#### Internal Security

Role-based access control controls the level of access for users of Apigee. Data masking and private variables can be used to prevent sensitive data from being visible when live traffic is being traced, and encrypted key value maps can be used to store and use configuration data like credentials, without allowing users of the Apigee platform to see the values. Role-based access control, or RBAC, provides controlled levels of access to users of the Apigee management platform. Tasks that can be performed in the management UI are the equivalent of one or more management API calls. 

Permissions are based on management API calls to resources. If the user can make an API call, she can perform the same action within the UI. Similarly, a user who does not have permission to make a management API call cannot perform the same action within the UI. Roles are used to group permissions. Roles can be assigned to users of the platform, and the user can have more than one role. When more than one role exists for a user, the user is able to perform any operation that either role is allowed to perform. Apigee comes with several predefined roles. Here are a few examples: an organization administrator, or org admin, is a superuser. A person with the org admin role has full control of the organization, and also can add users and custom roles to the organization. A read-only org admin has full read access to the organization. An operations administrator manages API deployments and troubleshoots proxies, and can deploy, test and trace APIs, but not create or edit them. A business user manages business entities like API products, developers, developer apps, and custom reports, but not API proxies or deployments.

A user is an API developer with the ability to edit API proxies. You may sometimes find that the built-in roles might not work for your use case. Apigee also provides the ability to create custom roles. You can create custom roles to customize permissions for your use cases. Use of the Apigee trace tool is vital for troubleshooting issues with your API. However, the user tracing live API traffic can by default see all of the fields that are being accessed during the API calls. This data can include sensitive user data, including names, passwords, or credit card numbers. 

A user can also see credentials that are being used to communicate with backend services. When you download a trace log, those values will also be in the trace file. Data masking can block configured data from being visible in live trace or trace files. You specify certain patterns of field or variable names, and matching data will be masked using a series of asterisks. Data masking is a feature that cannot be controlled using the Apigee management UI. Data masks can only be set up using the management API. Data masks can be configured at the organization level, and these masks will be active for all APIs in the organization. They can also be configured for a specific API proxy, adding additional fields to masks that are specific to the API. Because data masks are not visible in the UI, API teams sometimes forget about them. 

Protecting data is an important part of your API security, so you should create data masks for your organization and proxies, and ideally store the data masks in source control with your API proxies. Data masks are created by POSTing a request to the maskconfigs resource. The payload contains a list of variables and JSONPath or XPath expressions for API requests or responses. In this case, both the logonPassword field and the form parameter named creditcard of an incoming JSON request payload would be masked. When tracing, you will see the masked value replaced with asterisks. A downloaded trace file will also have the data masked.


### key-value-map-operations-policy   :  https://docs.apigee.com/api-platform/reference/policies/key-value-map-operations-policy


     <KeyValueMapOperations async="false" continueOnError="false" enabled="true"  name="KVM-GetCredentials" mapIdentifier="ProductsKVM">
           <ExclusiveCache>false</ExclusiveCache>
           <ExpiryTimeInSecs>60</ExpiryTimeInSecs>
              <Get assignTo="private.backendId">
                <Key>
                   <Parameter>backendId</Parameter>
                </Key>
             </Get>
             <Get assignTo="private.backendSecret">
            <Key>
              <Parameter>backendSecret</Parameter>
            </Key>
        </Get>
       <Scope>environment</Scope>
     </KeyValueMapOperations>


### BasicAuthentication policy : https://docs.apigee.com/api-platform/reference/policies/basic-authentication-policy
 
 
      <BasicAuthentication async="false" continueOnError="false" enabled="true" name="BA-AddAuthHeader">
          <Operation>Encode</Operation>
          <IgnoreUnresolvedVariables>false</IgnoreUnresolvedVariables>
          <User ref="private.backendId"/>
          <Password ref="private.backendSecret"/>
          <AssignTo createNew="false">request.header.Authorization</AssignTo>
      </BasicAuthentication>



### Data Masks API : https://apidocs.apigee.com/docs/data-masks/1/routes/organizations/%7Borg_name%7D/apis/%7Bapi_name%7D/maskconfigs/post

- https://apidocs.apigee.com/get-started
- https://github.com/apigee/apijam/blob/master/Module-2b/Labs/Lab%203/README.md
- https://docs.apigee.com/api-platform/faq/owasp-protection

----------------------------------------------

## Google Cloud - Apigee Certified API Engineer

Apigee Certified Professionals design and develop robust, secure, scalable API solutions that drive business objectives. This accreditation from Google certifies that you demonstrate a superior level of proficiency using Apigee products, processes, and practices, and that you can use the technology to help transform businesses and meaningfully impact the customers they serve.




| | | |
| :---:         |     :---      |          :--- |
| **Official Link:** | https://cloud.google.com/certification/apigee-api-engineer | 
| **Experience:  **  | Advanced-Professional | 
| **Certification:** | Specialization | 

### Posts

### Practice Exams / Tests

### Books
| Published | Title/Link | Author |
| :---:         |     :---      |          :--- |
| | [Official Ebooks](https://cloud.google.com/apigee/resources/#/type=Ebook) | |

### Videos / Sessions
| Event | Title/Link | Instructor |
| :---:         |     :---      |          :--- |
| Cloud Next '18 | [API Management Best Practices](https://www.youtube.com/watch?v=a_oPGpMfjMg) | |
| | [Official Webcasts](https://docs.apigee.com/) | |

### Online Trainings
| Site | Title/Link | Instructor |
| :---:         |     :---      |          :--- |
| Coursera | [Specialization Developing APIs with Google Cloud's Apigee API Platform](https://www.coursera.org/specializations/apigee-api-gcp) | |
| Coursera | [Official Training Program](https://cloud.google.com/training/apigee) | |

### Qwiklabs Links
|  Title/Link  |
| :---:         |
| [Using Apigee for API Management](https://google.qwiklabs.com/focuses/798?parent=catalog) |
| [App Modernization with Apigee](https://google.qwiklabs.com/quests/57) |


# test-task-for-build
a type of work and challenges that are aligned with our everyday tasks while supporting customers, business partners, and ISVs.

## Description of the task:
- please prepare a PoC solution (so understandably brief and with a limited functionality, reliability, recovery) that fulfills the following requirements and features:


### FR
- an application need to query the public API (accessible from any public site);
- need to page automatically through the pagination of the JSON pages produced by API (there are 20-40 results in a JSON array per page);
- the resulted records are stored in the destination - SaaS DB (NoSQL DB - Cloudant), or Object Storage;
- the refresh allows for checking for the new documents in the results and insert the delta in the destination storage - specified above


### NFR
- the application - an internal API needs to be container deployed in a K8s cluster or in OCP in IBM Cloud;
- the storage needs to be spun in IBM Cloud - IBM Cloudant, a K8s cluster, or Red Hat Openshift;


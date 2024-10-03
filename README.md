- Topic

  Development of Split Computing Orchestration Service

- Architecture
  ![image](https://github.com/user-attachments/assets/2c79f37f-1143-41ba-ac53-ec91a193d511)


- Description:
  This description outlines a system that splits the AlexNet model, containerizes model components, provides a user interface for deployment selection, and uses custom Karmada operators to automate the deployment process across multiple clusters.

  1. AlexNet model split into 5 head models and 5 tail models
  2. Each model file and inference API code dockerized (intermediate parameters from head model are sent to tail model)
  3. User selects desired model, edge, and core servers through UI, which automatically deploys models to respective clusters
  4. Karmada Operator
    - Two CRDs exist: Monitoring and AutoDeploy
    - When user selects appropriate model, edge, and core servers via UI, monitoring operator creates head-autoDeploy and tail-autoDeploy CRs
    - AutoDeploy CR automatically creates propagationpolicy and then auto-deploys deployment resources to each cluster

# FluentBit-ElasticSearch Kubernetes Deployment Example 
Example to create FluentBit setup on Kubernetes Cluster in order to connect FluentBit to ElasticSearch to generate logs for the whole Kubernetes Cluster 

##  Get Started 
1. Clone repo and move inside that directory

    ``` bash
    https://github.com/Shatabdi2621/FluentBit---ElasticSearch.git
    ```
2. Create a namespace (logging here in case)

    ``` bash    
    kubectl create ns <insert-namespace-name-here>
    ```

    eg

    ``` bash
    kubectl create ns logging
    ```

3. Switch to namespace logging 

    ``` bash
    kubectl config set-context --current --namespace=<insert-namespace-name-here>
    ```

    eg 

    ``` bash
    kubectl config set-context --current --namespace=logging
    ```

4. Start with deployment of files 

    a. Deployment of Service Account on Kubernetes Cluster 

    ``` bash
    kubectl apply -f .\service-account.yaml 
    ```

    b. Deployment of Cluster Role on Kubernetes Cluster 

    ``` bash
    kubectl apply -f .\cluster-role.yaml
    ```

    c. Deployment to Bind the Cluster Role to the Kubernetes Cluster 

    ``` bash
    kubectl apply -f .\cluster-role-bind.yaml 
    ```

    d. Deploy Config Map on the Kubernetes Cluster 
    
    ``` bash
    kubectl apply -f .\config-map.yaml
    ```
    **In file config-map.yaml the configuration to connect FluentBit to ElasticSearch may vary based on the requirement, you can visit the following link for more information on the configuration file "https://docs.fluentbit.io/manual/administration/configuring-fluent-bit/configuration-file"**
    
    e. Deploy the Daemon Set to Kubernetes Cluster 

    ``` bash
    kubectl apply -f .\daemon-set.yaml
    ```

    Replace 
    - ${FLUENT_ELASTICSEARCH_HOST}
    - ${FLUENT_ELASTICSEARCH_PORT}
    - ${FLUENT_ELASTICSEARCH_HTTP_User}
    - ${FLUENT_ELASTICSEARCH_HTTP_Passwd}
    with your information from your cluster 

    For more detailed information on the above operation please follow the link given below :
    "https://medium.com/kubernetes-tutorials/exporting-kubernetes-logs-to-elasticsearch-using-fluent-bit-758e8de606af" 

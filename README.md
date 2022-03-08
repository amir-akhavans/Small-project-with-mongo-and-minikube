## How to run this small project with mongo and minikube:

I used single node kubernetes cluster using mikikube so first install minikube and kubectl in your local host. 
When you have installed these prerequisites, test your minikube cluster using this command line:

'minikube status'

If everuthing with this cluster is ok, you will see running massage. 
You also can check its provisiond nodes's status to make sure everything with this node is ok or not using this command line: 

'kubectl get nodes'

it shows node's status. If everything is ok, status READY shows up.
After minikube and cubectl runs successfully, in order to run my code, since the secret-file.yaml and configMap.yaml are referenced in mongodb and mongoExpress codes, you need to apply them first using this command lines:

'kubectl apply -f secret-file.yaml'
'kubectl apply -f configMap.yaml'

after applying these two files, apply the rest of files to run the mongo database. 

It should be noted that I assigned port number 30000 to nodePort so you can see the output entering the 127.0.0.1:30000 in your web browser.

If this http connection could not be established, you have to forword this service to another port using the following command line, I assigned port 8080.

'kubectl port-forward svc/mongo-external 8080:8081'

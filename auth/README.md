# Steps in back end for auth service setup

* Create a auth folder, then go inside the auth folder and run npm init -y

* Then run npm install typescript ts-node-dev express @types/express inside the auth folder

* Then run tsc --init inside the auth folder to create a new tsconfig.json file

* Then add start script in package.json file "start": "ts-node-dev src/index.ts"

* IMP - Create .gitnore file under auth folder BEFORE ANY COMMIT and Add node_modules/ & .env into that file

* Then run npm start to check whether auth server is running

# Steps in back end for auth kubernetes service setup

* We need to build an image out of the auth service , in order to build the image we need to create a dockerfile for auth service

* We dont really want to load up node_modules folder into our container as it's being built, so we need to create .dockerignore file inside auth directory.

* Now we need to build this auth image by running the command in terminal - docker build -t dockerid/auth .

* So now we're going to start to put together a little bit more configuration to get that image loaded up into a Kubernetes cluster. To get that image running. We're going to create remember, it is called a deployment. A deployment is going to create a set of pods for us automatically. And we can make sure that those pods are running our auth service. So we need to write out a Kubernetes config file. Create a new folder inside ticketing directory called Infra (Short for Infrastructure). Inside infra create new folder inside there called K8s. And then inside that folder make a new file called auth-depl.yaml file.

# Steps in back end for ticketing app to set up our scaffold config file.

* The scaffold config file is going to watch our infra directory. Any time we make a change to a config file, it will automatically apply it to our cluster. It's also going to make sure that any time we change any code inside of our auth directory, it will sync all the files inside there with the appropriate running container inside of our cluster. So to create our scaffold config file, I'm going to find my root project directory and inside there we will create another file called scaffold.yaml file.

* In terminal goto your ticketing directory and run skaffold dev there

* After running skaffold dev in terminal, I am getting error related to minikube. So I chacked the status of minkube by riunning minikube status in terminal and if it is stopped run minikube start in terminal. 

* Now run skaffold dev in terminal under ticketing folder

* Now if the skaffold dev is running, so now make changes to your auth index.ts express file like - 
```
console.log('Listening on port 3000!!!!!!')
```
and see if that changes are reflecting in the skaffold terminal

* If you did not see your server restart after changing the index.ts file, do the following: 
  
1. Open the package.json file in the ‘auth’ directory

2. Find the ‘start’ script

Update the start script to the following:

```
ts-node-dev --poll src/index.ts
```

# Steps in back end for auth to set up ingress-nginx.

* Add a get route for current user just to check in index.ts epress file.

* I will see that my auth server is automatically restarted becuase of the skaffold dev, it is watching for changes everytime

* Now we need to access our running server specifically our auth pod. To access anything inside of our cluster, we have to set up one of two things. We really have two options. We can either set up one of those node port services or we can set up that ingress service. Remember that ingress is all about having some routing rules tied to nginx, so at any time a request comes into our cluster, it'll be handled by that ingress service. They'll be routed off to the appropriate service within our cluster. So we will create a new file inside our infra/k8s directory ingress-serv.yaml.
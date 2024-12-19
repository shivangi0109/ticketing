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

* So now we're going to start to put together a little bit more configuration to get that image loaded up into a Kubernetes cluster. To get that image running. We're going to create remember, it is called a deployment. A deployment is going to create a set of pods for us automatically. And we can make sure that those pods are running our auth service.
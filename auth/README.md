# Steps in back end for auth

* Create a auth folder, then go inside the auth folder and run npm init -y

* Then run npm install typescript ts-node-dev express @types/express inside the auth folder

* Then run tsc --init inside the auth folder to create a new tsconfig.json file

* Then add start script in package.json file "start": "ts-node-dev src/index.ts"

* IMP - Create .gitnore file under auth folder BEFORE ANY COMMIT and Add node_modules/ & .env into that file

* Then run npm start to check whether auth server is running
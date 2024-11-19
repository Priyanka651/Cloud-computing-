Here's a revised version of the README file that includes the steps you provided, ensuring all the details match your project steps:


## MongoDB + Python Flask Web Framework + REST API + GKE ##

This project involves creating a MongoDB database using persistent volume on GKE, deploying a Python Flask web application and a Node.js server to fetch records from MongoDB, and exposing these applications using Ingress with Nginx. The project is divided into several steps, detailed below.

## MongoDB Deployment on GKE ##

**Step 1: Create MongoDB Using Persistent Volume on GKE and Insert Records**

1.**Create a GKE Cluster:**

gcloud container clusters create kubia --num-nodes=1 --machine-type=e2-micro --region=us-west1

Wait for the cluster creation to finish.

**2.Create Persistent Volume:**

gcloud compute disks create --size=10GiB --zone=us-west1-a mongodb

**3.Deploy MongoDB: Apply the mongodb-deployment.yaml configuration:**
     ## Deploy MongoDB on Kubernetes

To deploy MongoDB on Kubernetes, apply the `mongodb-deployment.yaml` configuration:

```yaml
apiVersion: v1
kind: PersistentVolume
metadata:
  name: mongodb-pv
spec:
  capacity:
    storage: 10Gi
  accessModes:
    - ReadWriteOnce
  gcePersistentDisk:
    pdName: mongodb
    fsType: ext4
---
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: mongodb-pvc
spec:
  accessModes:
    - ReadWriteOnce
  resources:
    requests:
      storage: 10Gi
---
apiVersion: apps/v1
kind: Deployment
metadata:
  name: mongodb-deployment
spec:
  selector:
    matchLabels:
      app: mongodb
  strategy:
    type: Recreate
  template:
    metadata:
      labels:
        app: mongodb
    spec:
      containers:
      - image: mongo
        name: mongo
        ports:
        - containerPort: 27017
        volumeMounts:
        - name: mongodb-data
          mountPath: /data/db
      volumes:
      - name: mongodb-data
        persistentVolumeClaim:
          claimName: mongodb-pvc

kubectl apply -f mongodb-deployment.yaml

4. **Check Deployment Status:**
     ```bash
    kubectl get pods
       ```
    Ensure the pod status is `Running`.

5. **Create MongoDB Service:**
     Apply the `mongodb-service.yaml` configuration:
    ```yaml
    apiVersion: v1
    kind: Service
    metadata:
      name: mongodb-service
    spec:
      type: LoadBalancer
      ports:
      - port: 27017
        targetPort: 27017
      selector:
        app: mongodb
    ```
    ```bash
    kubectl apply -f mongodb-service.yaml
    ```
6. **Verify Service Status:**
    ```bash
    kubectl get svc
    ```
    Wait for the `EXTERNAL-IP` to be assigned.

7. **Test MongoDB Connection:**
    ```bash
    kubectl exec -it mongodb-deployment-replace-with-your-pod-name -- bash
    ```
8.**Insert Records into MongoDB:**
    Use the following Node.js script to insert data into MongoDB:
    ```javascript
    const { MongoClient } = require('mongodb');

    async function run() {
      const url = "mongodb://<EXTERNAL-IP>/studentdb"; // Use the correct IP and port
      const client = new MongoClient(url, { useNewUrlParser: true, useUnifiedTopology: true });

      try {
        await client.connect();
        const db = client.db("studentdb");
        const collection = db.collection("students");

        const docs = [
          { student_id: 11111, student_name: "Bruce Lee", grade: 84 },
          { student_id: 22222, student_name: "Jackie Chan", grade: 93 },
          { student_id: 33333, student_name: "Jet Li", grade: 88 }
        ];

        const insertResult = await collection.insertMany(docs);
        console.log(`${insertResult.insertedCount} documents were inserted`);

        const result = await collection.findOne({ student_id: 11111 });
        console.log(result);
      } finally {
        await client.close();
      }
    }
    run().catch(console.dir);
    ```

## StudentServer Setup

### Step 2: Modify StudentServer to Fetch Records from MongoDB and Deploy to GKE

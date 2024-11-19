Here's a revised version of the README file that includes the steps you provided, ensuring all the details match your project steps:


**MongoDB + Python Flask Web Framework + REST API + GKE**
This project involves creating a MongoDB database using persistent volume on GKE, deploying a Python Flask web application and a Node.js server to fetch records from MongoDB, and exposing these applications using Ingress with Nginx. The project is divided into several steps, detailed below.

**MongoDB Deployment on GKE**
Step 1: **Create a GKE Cluster:**
gcloud container clusters create kubia --num-nodes=1 --machine-type=e2-micro --region=us-west1

Wait for the cluster creation to finish.

## Project Description

This project deploys a Streamlit-based video transcription and chat application inside a Docker container. It utilizes OpenAI's Whisper model for transcription, Pinecone for vector database storage, and GPT for chat capabilities. The application provides users with an easy way to transcribe YouTube videos and interact with the transcripts through chat.

## Prerequisites


Before starting, ensure you have the following:  
- **OpenAI API Key**: Obtainable from [OpenAI's API Dashboard](https://platform.openai.com/).  
- **Pinecone API Key**: Obtainable from [Pinecone Dashboard](https://www.pinecone.io/).  
- **Docker Desktop**: Install the latest version from [Docker's official site](https://www.docker.com/products/docker-desktop).  
- **GitHub Repository**: Clone the required repository.  

---

## Steps to Deploy  

### 1. Clone the Repository  
Open your terminal and run the following command:  
```bash  
git clone https://github.com/Davidnet/docker-genai.git  
2. Obtain API Keys
OpenAI API Key:

Go to OpenAI's API Dashboard.
Log in and navigate to API Keys.
Click Create new secret key, name it, and copy the key.
Pinecone API Key:

Search "Pinecone" in Google Cloud and click Subscribe.
Sign up on the Pinecone website with your email.
Go to the API Keys section and copy the key.
3. Specify API Keys in the Environment File
Navigate to the project directory:

bash
Copy code
cd docker-genai  
Create a .env file:

bash
Copy code
vim .env  
Add the following content to the .env file, replacing your-api-key with your actual API keys:

plaintext
Copy code
#----------------------------------------------------------------------------  
# OpenAI  
#----------------------------------------------------------------------------  
OPENAI_TOKEN=your-api-key # Replace with your OpenAI API key  

#----------------------------------------------------------------------------  
# Pinecone  
#----------------------------------------------------------------------------  
PINECONE_TOKEN=your-api-key # Replace with your Pinecone API key  
4. Build and Run the Application
Run the following command to build and start the application:

bash
Copy code
docker compose up --build  
5. Access the Services
Video Transcription Service:
Open a browser and visit http://localhost:8503.

Input a YouTube video URL.
Click Submit to transcribe the video using the Whisper model.
Chat Service:
Access the chat service at http://localhost:8504.

Interact with the transcribed video content by asking questions.
Responses are generated using GPT and Pinecone.
6. Stop the Application
To stop the application, go back to the terminal where the app is running and press:

bash
Copy code
Ctrl + C  




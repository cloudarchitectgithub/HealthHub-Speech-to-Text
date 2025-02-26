# Implementation of Functionality To Convert Audio Conversation Between Doctors And Patients into Text Using The Azure AI Speech Service

<p align="center">
<img src="https://i.imgur.com/d7QnuHH.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

## Project Description

The HealthHub Speech-to-Text Project implements a system that converts audio conversations between doctors and patients into text using Azure AI Speech Service. The system integrates several AWS components, including Amazon Cognito for secure authentication, S3 for hosting the frontend, API Gateway and Lambda for backend processing, and DynamoDB for data storage. The system is monitored using AWS CloudWatch, and resource provisioning is handled by AWS CloudFormation. The solution ensures scalability, security, and efficiency in transcribing medical conversations, which are then saved to the patient's medical record.

<p align="center">
<img src="https://i.imgur.com/ppRK8kr.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

Monitoring is handled via CloudWatch, and the architecture leverages CloudFormation for resource provisioning, ensuring a scalable and efficient workflow for medical audio transcription.

## Project Objectives

1. **Develop a Secure and Scalable Solution**: Implement a system that utilizes Azure AI Speech Service and AWS's serverless architecture for processing and storing medical transcription data securely.
2. **Enable Multilingual Transcriptions**: Test and support audio transcription in multiple languages, including English and Portuguese, to accommodate diverse user needs.
3. **Streamline Medical Record Management**: Provide healthcare professionals with accurate, efficient transcription capabilities to enhance patient care.
4. **Ensure Compliance**: Adhere to best practices for handling sensitive medical records, ensuring security, compliance, and confidentiality.
5. **Deploy, Test, and Validate Functionalities**: Implement rigorous testing protocols to validate all features, including backend processing and front-end usability.

## Project Solution

### Solution Part 1: Backend Implementation

1. **Azure AI Speech Service Setup**:
   - Create an Azure Speech resource in the Central US region.
   - Retrieve and store the API key and endpoint securely for integration.
2. **Backend Preparation and Deployment**:
   - Start the AWS EC2 instance.
   - Download application files (backend and frontend).
   - Use npm install to set up the backend dependencies.
   - Configure Azure service credentials (key and region) in environment variables.
3. **Service Deployment and Testing**:
   - Deploy the transcription service using npm run deploy.
   - Test backend functionality to transcribe doctor-patient conversations.
   - Validate transcriptions for English and Portuguese languages by saving results to medical records.
4. **Monitoring and Metrics**:
   - Leverage Azure AI's monitoring dashboard to analyze API calls and performance metrics.

### Solution Part 2: Frontend Implementation

1. **Frontend Preparation**:
   - Navigate to the frontend folder and run npm install to install dependencies.
   - Set up the API Gateway URL in the .env file.
2. **Application Deployment and Testing**:
   - Launch the frontend application using npm run dev --host.
   - Register profiles for doctors and patients.
   - Test transcription functionality by uploading and processing audio files in the supported languages.
3. **Validation and Evidence Collection**:
   - Verify saved transcriptions in the patient's medical record.
   - Collect screenshots of functionality as evidence for project documentation.
4. **Resource Cleanup**:
   - Use sls remove and related commands to remove all deployed resources.
   - Delete residual files and stop the EC2 instance.

## Tools and Technologies

- **Microsoft Azure**:
  - Azure AI Speech Service: For transcribing audio into text.

- **AWS**:
  - Amazon Cognito: For user authentication.
  - Amazon S3: For hosting the frontend application.
  - AWS API Gateway: For routing requests to the backend.
  - AWS Lambda: For backend processing.
  - Amazon DynamoDB: For storing medical records.
  - AWS CloudWatch: For monitoring the services and resources.
  - AWS CloudFormation: For provisioning and managing infrastructure as code.
- **Node.js & Serverless Framework**: For deploying the backend services.
- **Docker**: For containerizing the application and backend services.

## Step-by-Step Directions

### Step 1: Set Up Azure AI Speech Service

1. **Create the Azure Speech Service**:
   - Open the Azure portal and navigate to "Azure AI Services".

<p align="center">
<img src="https://i.imgur.com/WsO4MQq.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

<p align="center">
<img src="https://i.imgur.com/FeL2u65.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

   - Create a new Speech Service resource:
     - Resource Group: AI-Speech-Service_rg

<p align="center">
<img src="https://i.imgur.com/IiRa8ij.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

     - Region: Central US (or another region with free tier availability).

<p align="center">
<img src="https://i.imgur.com/57R66c7.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

     - Name: tcb-ai-speech-svc-YOUR-NAME

<p align="center">
<img src="https://i.imgur.com/duyvB8c.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

     - Pricing Tier: Free F0 (Free tier for up to 500 pages/month).

<p align="center">
<img src="https://i.imgur.com/RwPCNv9.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

   - Save the Key and Endpoint for the service.

<p align="center">
<img src="https://i.imgur.com/5iERPGh.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

<p align="center">
<img src="https://i.imgur.com/Kc3jhbb.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

### Step 2: Prepare Backend Development Environment

1. **Start your virtual machine or instance and connect to it**.

<p align="center">
<img src="https://i.imgur.com/vvs1OBG.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

2. **Download the project files by**:
   - Download and unzip these files into the appropriate directory.

<p align="center">
<img src="https://i.imgur.com/piQ2lnE.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

### Step 3: Install Backend Dependencies

1. **Navigate to the backend folder**.

<p align="center">
<img src="https://i.imgur.com/0e5qvAD.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

2. **Run the following command to install dependencies**:

<p align="center">
<img src="https://i.imgur.com/hNHtEax.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

### Step 4: Configure Azure Credentials

1. **In the `src/services/transcription-service/serverless.yml` file, add yours Azure Speech Service credentials**:

<p align="center">
<img src="https://i.imgur.com/tvpKEgI.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

<p align="center">
<img src="https://i.imgur.com/IIOq3Go.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

- Note: These key can be pass on to the developer, so the developer can access in a simple way.

2. **Input the following details**:
   - Azure Speech Key: The key copied from the Azure Speech Service.
   - Azure Speech Region: The selected Azure region (e.g., Central US).

<p align="center">
<img src="https://i.imgur.com/Ldx0ZaU.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

<p align="center">
<img src="https://i.imgur.com/hCkPIz0.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

3. **Save and exit the file**.

### Step 5: Deploy the Backend Service

- **Deploy the backend service using the following command**:

<p align="center">
<img src="https://i.imgur.com/dy8t6Jl.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

- This process deploys the transcription service that converts audio conversations into text.
- Verify successful deployment by monitoring logs and checking outputs in the console.

### Step 6: Validate Backend Configuration

- **Test backend functionality by confirming**:
  - Environment variables are set up correctly.

<p align="center">
<img src="https://i.imgur.com/pvAXnVh.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

<p align="center">
<img src="https://i.imgur.com/tCpwLNs.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

  - Deployment logs show no errors.

<p align="center">
<img src="https://i.imgur.com/wpzVYB8.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

  - Transcription service is active and configured properly.

## Solution Part 2: Frontend Implementation

### Step 1: Prepare Frontend Development Environment

1. **Exit the backend directory and navigate to the frontend folder**.

<p align="center">
<img src="https://i.imgur.com/r51SgZH.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

2. **Use the following command to install frontend dependencies**:

<p align="center">
<img src="https://i.imgur.com/p62Pnyd.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

### Step 2: Configure Frontend Application

1. **Copy the API Gateway URL created during the backend deployment**.
2. **Open the .env file in the frontend directory**:

<p align="center">
<img src="https://i.imgur.com/1fm5LRJ.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

<p align="center">
<img src="https://i.imgur.com/BfM3Zup.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

3. **Add the API Gateway URL under the appropriate variable**.

<p align="center">
<img src="https://i.imgur.com/DDbdxlM.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

4. **Save and exit the file**.

### Step 3: Start the Frontend Application

1. **Launch the application by running the following command**:
   ```
   npm run dev --host
   ```
2. **Access the application via the browser by navigating to**:

<p align="center">
<img src="https://i.imgur.com/OiPNWKk.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

<p align="center">
<img src="https://i.imgur.com/sTqflcr.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

### Step 4: Test Frontend Functionality

1. **Register Users**
   - Register a doctor and patient within the application.

<p align="center">
<img src="https://i.imgur.com/3MMf8Ec.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

<p align="center">
<img src="https://i.imgur.com/2wW8czQ.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

2. **Perform Transcriptions**
   - Log in as a doctor and test the Transcribe Audio feature.
   - Upload WAV files in Portuguese and English for transcription.

<p align="center">
<img src="https://i.imgur.com/FjKDmNr.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

<p align="center">
<img src="https://i.imgur.com/Uyqho1w.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

3. **Validate Transcriptions**
   - Check that transcriptions are saved in the patient's medical record.
   - Ensure accurate conversion of audio to text.

<p align="center">
<img src="https://i.imgur.com/WZ8CHPk.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

<p align="center">
<img src="https://i.imgur.com/q4TXX4n.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

4. **Monitor Azure Metrics**
   - Access the Azure Speech Service resource.
   - Verify metrics, including successful API calls and audio transcription rates.

<p align="center">
<img src="https://i.imgur.com/aQgaWJK.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

### Step 5: Document Testing Evidence

1. **Take screenshots of**:
   - The doctor's dashboard with the transcription options.
   - The patient's medical record displaying transcriptions in both languages.

<p align="center">
<img src="https://i.imgur.com/UMS2kRe.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

<p align="center">
<img src="https://i.imgur.com/3ROJ8Ji.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

## Next Steps

Following the completion of this project, the next module will focus on implementing the Health Hub's Image Analysis Module using Google Cloud AI Services. This transition highlights the interoperability and scalability of cloud-based AI solutions in healthcare.

## Project Conclusion

The project successfully demonstrated the integration of Azure AI Speech Service with an AWS-based backend to create a scalable and efficient system for transcribing doctor-patient audio conversations. By leveraging the strengths of both platforms, the solution enabled seamless transcription and storage of medical records, ensuring accessibility and accuracy. Key AWS components such as Lambda, DynamoDB, and API Gateway worked in harmony with Azure Speech Service, highlighting the effectiveness of a multi-cloud approach. Despite challenges such as managing cross-platform configurations and addressing deployment errors, the project achieved its objectives, delivering a functional, cost-effective, and reliable solution. The experience underscored the importance of rigorous testing, monitoring, and strategic resource placement to optimize performance in multi-cloud environments.

## Challenges Encountered

1. **Credential Management**: Safeguarding API keys and configuring secure access.
2. **Multilingual Support**: Ensuring accurate transcription and translation in two languages.
3. **Latency Issues**: Observed minor delays in processing with free-tier services.
4. **Resource Management**: Efficiently deploying and cleaning up cloud resources.
5. **File Format Constraints**: Restricting uploads to WAV format under 5MB.

## Lessons Learned

1. **Importance of modular development** for managing multi-phase implementations.
2. **Benefits of cross-platform integrations** in leveraging the best features of Azure and AWS.
3. **Significance of robust monitoring** to ensure service reliability.
4. **Necessity of clear documentation** for reproducible deployments.

## Future Improvements

1. **Expand Language Support**: Add support for additional languages to cater to a broader user base.
2. **Enhanced User Interface**: Create a more intuitive and responsive design for end users.
3. **Advanced Analytics**: Integrate AI models to analyze transcription data for medical insights.
4. **Real-Time Processing**: Implement real-time audio transcription and translation.
5. **Scalability Enhancements**: Optimize deployments to handle high traffic seamlessly.
6. **Compliance Automation**: Build features to automate HIPAA and GDPR compliance reporting.

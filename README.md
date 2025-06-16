# A-Image-Hiding-and-Extraction-process-using-AES-and-LSB-Algorithms
Product Requirements Document (PRD)

Project Title: Secure Image Steganography using AES Encryption & LSB Steganography
Version: 1.0
Authors: Vadla Saichandu

    Introduction 1.1 Purpose

Develop a secure system to:

Hide a secret image inside a cover image using AES encryption (for security) and LSB steganography (for embedding).

Extract and decrypt the hidden image with high fidelity.

1.2 Target Users

Security researchers, forensic analysts, and privacy-conscious individuals.

2. Technical Requirements
2.1 Functional Requirements
ID	Requirement	Implementation
FR1	Encrypt secret image using AES-256 (Python/Matlab)	PyCryptodome (Python) / AES Toolbox (Matlab)
FR2	Embed encrypted data into cover image using LSB	LSB substitution (Python/Matlab)
FR3	Extract hidden data from stego-image	LSB decoding (Python/Matlab)
FR4	Decrypt extracted data using AES-256	PyCryptodome (Python) / AES Toolbox (Matlab)
FR5	GUI for user interaction (Python)	Tkinter (Python) / App Designer (Matlab)
2.2 Non-Functional Requirements

Security: AES-256 encryption for confidentiality.

Performance: Processing time < 5s for 512x512 images.

Accuracy: 100% recovery of hidden image post-extraction.

3. System Design
3.1 Workflow

Encryption:
python

from Crypto.Cipher import AES
cipher = AES.new(key, AES.MODE_EAX)
ciphertext, tag = cipher.encrypt_and_digest(secret_image_bytes)

LSB Embedding:

Replace LSBs of cover image pixels with ciphertext bits.

Extraction:

Read LSBs from stego-image to recover ciphertext.

Decryption:
python

cipher = AES.new(key, AES.MODE_EAX, nonce)  
plaintext = cipher.decrypt(ciphertext)  

3.2 MATLAB Components

Use Image Processing Toolbox for LSB and AES Toolbox for encryption.

4. Tools & Libraries
Component	Python	MATLAB
AES	PyCryptodome	AES Toolbox
LSB	Custom logic	bitget/bitset
GUI	Tkinter	App Designer
5. Test Cases
Scenario	Input	Expected Output
Valid Encryption	Secret image + Key	AES-encrypted bytes
LSB Embedding	Cover image + Encrypted data	Stego-image (PSNR > 30dB)
Full Pipeline	Cover + Secret image	Recovered secret image (100% match)
6. Deliverables

Python Implementation:

    Jupyter notebook with CLI/GUI.

    Dockerfile for deployment.

MATLAB Implementation:

    .m scripts + GUI (App Designer).

Documentation:

    User manual + PR

    D.

7. Timeline
Phase	Duration
Research	1 week
Python MVP	2 weeks
MATLAB Porting	1 week
Testing	1 week

Based on your PRD for secure image steganography, I'll create a comprehensive web application that implements AES-256 encryption with LSB steganography. This will be a production-ready system with an intuitive interface for hiding and extracting secret images.

Core Features:

    AES-256-GCM encryption for maximum security of secret images
    LSB (Least Significant Bit) steganography for seamless embedding
    Real-time image processing with progress indicators
    Dual-mode operation: Hide (embed) and Extract (reveal) workflows
    Image preview and comparison capabilities
    Secure key generation and management
    Download functionality for processed images
    Error handling and validation throughout the process

Design Elements:

    Clean, professional interface with step-by-step workflow guidance
    Color system with primary blue (#2563eb), secondary purple (#7c3aed), accent green (#10b981), plus warning and error states
    Smooth animations for file uploads, processing states, and transitions
    Responsive design optimized for desktop and tablet usage
    Modern card-based layout with subtle shadows and gradients
    Interactive hover states and micro-interactions for enhanced user experience

Secure Image Steganography Application

npm install

src/App.tsx
src/components/HideImagePanel.tsx
src/components/ExtractImagePanel.tsx
src/components/ImageUploader.tsx
src/components/ProcessingProgress.tsx
src/components/PasswordInput.tsx
src/utils/steganography.ts

    npm run dev

I've created SecureStego, a comprehensive web application for secure image steganography that implements your PRD requirements. The system uses AES-256-GCM encryption combined with LSB steganography to provide maximum security for hiding secret images.

The application features a dual-mode interface where users can either hide images (encrypt and embed) or extract images (extract and decrypt) with step-by-step guidance. It includes real-time processing indicators, comprehensive error handling, and a professional UI that guides users through the entire workflow. The system validates password strength, provides image previews, and includes secure download functionality for processed images.

Deploy this application.

I'll help you deploy this application to Netlify.
Deploy application to Netlify

npx vite build

netlify
Open website

    npm run dev

I've initiated the deployment process. Let me check the deployment status for you...

Your site has been successfully deployed! You can view it at: https://eloquent-belekoy-29eb43.netlify.app

To transfer this Netlify project to your own account, you can use  this claim URL:
https://app.netlify.com/claim?utm_source=bolt#eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJjbGllbnRfaWQiOiI1aDZmZEstVktNTXZuRjNiRlZUaktfU2JKVGgzNlNfMjJheTlpTHhVX0Q4Iiwic2Vzc2lvbl9pZCI6IjUwMDUzNTMxOjUzNTU0MjkiLCJpYXQiOjE3NTAwNTk2NDl9.RVcOsgqtsOH9CpfIcPqn4Uhpw_omay88PQns2U-jYqU
96K daily tokens remaining.
// AES encryption utilities using Web Crypto API
    // Decrypt the extracted data
    const decryptedData = await CryptoUtils.decrypt(encryptedData, password);
    onProgress(75);

    // Convert decrypted data back to image
    const blob = new Blob([decryptedData]);
    const imageUrl = URL.createObjectURL(blob);
    onProgress(100);

    return imageUrl;
  } catch (error) {
    throw new Error('Failed to decrypt data. Please check your password and ensure the image contains hidden data.');
  }
}

# AES Encrypting the Image into Binary data(Cover image )

![image](https://github.com/user-attachments/assets/3b51da71-3d98-4449-9c21-d84e06dc253b)

![image](https://github.com/user-attachments/assets/5cbebabd-2eb2-489f-a314-f314238df837)

# Extracting the Image(Converted Stego-image into Pixels format)

![image](https://github.com/user-attachments/assets/04f60a15-1077-41ea-847b-e263587ca952)




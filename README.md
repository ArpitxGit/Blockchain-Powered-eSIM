# Blockchain-Powered-eSIM

## - What is the product?
    - This is not a stand alone product, we want to deliver an alternate product to telecom network providers who already carry eSIM infrastructure and provide eSIM to end users.
    - We will not be dealing with end users directly.
    - Our role is to provide the end users with a novel way of using eSIM services that enables them to do more than just communicate.
    - This also provides users the option to use a network without trusting the network provider.

## Three main touchpoints:

# 1) User Authentication/Onboarding

- First step user need to take to avail this service
    - User will buy an eSIM from existing telecom operators by providing their KYC and preferred wallet address(if they have one) and that’s it!
- What happens in the backend?
    - We’ll provide a portal to the telecom operator where the user will provide the above two information.
    - Now, with this information we will get a unique ZK identity which will be used for all communication protocols.
    - And once the user authentication is completed a smart contract will be deployed
        - This smart contract will be the basis to all the transactions and the connectivity to the decentralized ecosystem(i. e, using decentralized applications).
    - By creating this layer we are disconnecting user identification from user activity.
        - The telecom operators will have the user identity,
        - And we’ll have the activity log,
        - Thus, no party has both.
    - Resulting in the removal of the need to trust the telecom operator for user personal information and activity.

Our main challenge here is to create a communication protocol that can uses the ZK identity and existing network infrastructure to connect two users.

The current communication technology that allows communication between two users is known as Global System for Mobile Communications by using Session Initiation Protocol (SIP).

Now that we know what kinds of network packets we need to create as part of this communication protocol, we move to the device.

# 2) Establishing secure connection to device through LPA

- The Local Profile Assistant (LPA),
         A software component that runs on the device and interacts with eSIM chip.
    - The LPA will pick users’ ZK identity from the blockchain and store this in a tokenized form on the eUICC module.
    - The LPA will be accompanied by a UI, called LUI
        - This will be the application that the end users will interact with to manage their:
            - eSIM Profile
            - Communication Plans
            - Blockchain Services
- The LPA will be responsible for all communication to the device and the OS
    - This will be the layer that brings our eSIM ecosystem to life.
- Interaction to Android or OS services
    - The LPA will broadly be probing five OS services:
        - Euicc Service || Management of eSIM profiles through ISD-R (”Issuer Security Domain Root”, i. e, the security layer) ||| Kernel Level Implementation
            - The ISD-R serves as the root of trust for the eSIM, providing the highest level of security and control.
            - The ISD-R is responsible for managing and controlling access to other security domains within the secure element.
            - Also provides secure storage for cryptographic keys, certificates, and other sensitive data used by the secure element.
        - Connectivity Manager || Modem
            - Will deploy the algorithm that will intercept network traffic,
            - Entangle the network traffic with our ZK Identity to establish unique and encrypted connections between users as well as services
        - Telephony Manager || Dialer
            - Provides access to telephony-related information and services on devices.
        - Account Manager
            - This service will make use of the tokenized ZK identity to establish authentication which will be used to access all blockchain based features
        - Security APIs
            - This layer verifies that the transactions were initiated or executed by the owner of the smart contract or not.
            - Our modifications to the APIs will ensure that all the transactions, communication or any interaction otherwise involving our eSIM product is secure and encrypted.

# 3) Establishing secure connection to network

### a) Telecom Network

- The device sends a request to the eSIM provider to register on a specific network.
    - The request is sent in form of device identifying network credentials.
    - The registration is done by authenticating these network credentials.
- The eSIM provider then sends a request to the network to allow the device to register on the network.
    - The network operator performs a verification process to ensure that the device is authorized to access the network.
    - By checking the device's IMEI (International Mobile Equipment Identity) number and other identifying information to make sure the device is not stolen or being used for illegal purposes.
- Once the network has authorized the device, the eSIM provider sends the necessary network credentials to the device, which can then establish a connection to the network.
    - These credentials includes:
        - The network's access code,
        - Encryption keys,
        - And other information needed to establish a connection to the network.

And all these Management of the device's profile and network credentials is done by the LPA,

- LPA sends a request to the eSIM provider to download the network profile onto the eSIM chip.
- The eSIM provider then sends the network profile to the LPA, which securely stores the profile on the eSIM chip.

The protocols that are involved in this process are:

- Remote SIM Provisioning (RSP): This is a standard that enables over-the-air management of eSIMs, allowing them to be programmed remotely by an authorized party, such as the eSIM provider.
- Subscription Manager Data Preparation (SMDP): This is a server-side system used by the eSIM provider to manage the eSIM profiles and credentials. It communicates with the device's LPA to download and install network profiles.
- Profile Manager: This is the software component that runs on the device's LPA and manages the eSIM profile and credentials. It communicates with the SMDP to download network profiles and activate them on the eSIM chip.
- HTTPS (Hypertext Transfer Protocol Secure): This is the protocol used for secure communication between the device, the eSIM provider, and the SMDP. It ensures that all data transmissions are encrypted and secure.
- GSMA Remote SIM Provisioning Architecture (RSP-A): This is a technical architecture developed by the GSMA (GSM Association) that defines the standards and protocols for remote provisioning of eSIMs.

### b) Blockchain Network

- Connection to an Ethereum node to communicate with the Ethereum blockchain network.
    - Choose an Ethereum client implementation that fits in the tech stack.
    - Installing and configuration the Ethereum client
    - Choose a library or tool that supports JSON-RPC communication as the Ethereum network uses the JSON-RPC protocol to communicate with clients.
    - Connect to the Ethereum node by specifying the IP address or domain name of the node and the port number to use.
    - Authentication and authorization the connection before the establishment of communication with the Ethereum network.

# Challenges

## Theoretical

- How to fetch user data from the blockchain without internet connectivity?
- How to make the Security Layer fool proof, the Security APIs?
- How to establishing a secure connection to blockchain network?
- How to serve a cryptographic wallet address that has the allowance of connectivity and execution of transactions on multiple blockchain?
- How to ensure the scalability of the blockchain network while maintaining its security?
- How to maintain the integrity of smart contracts on the blockchain network?
- How to ensure interoperability between different blockchain networks?
- How to handle network congestion on the blockchain network?
- How to maintain data consistency across the blockchain network?
- How to ensure regulatory compliance while using a decentralized platform like blockchain?
- How to prevent fraud and malicious attacks on the blockchain network?

## Implementation

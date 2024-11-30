# **Essa-NPZ: A Secure Decentralized Communication Platform**

---

## **Introduction**

Essa-NPZ is a secure, decentralized messaging application built on the NPZ (Network Protocol Zero) protocol. Designed for privacy and efficiency, Essa-NPZ ensures that:

- **Servers act only as intermediaries**, routing messages without storing them.
- **End-to-end encryption** secures all communications using public/private key pairs.
- **Users can host their own servers**, promoting decentralization and control.
- **Messages and files are routed efficiently** through NPZ's hierarchical addressing.
- **Modified network protocols are used for routing**, enhancing performance and security.

---

## **Key Features**

### **1. Decentralized Server Architecture**

- **Unique Server Addresses**:
  - Each server is identified by a unique NPZ address (e.g., `XXX.YYY.ZZZ.VVV`).
  - Servers act as intermediaries for routing messages, without storing any data.

- **Server Verification**:
  - **Servers verify if a given NPZ address exists in a specific location** before routing messages.
  - This ensures accurate delivery and efficient use of network resources.

- **User-Hosted Servers**:
  - Any user can set up their own server for added control.
  - Decentralized routing ensures reliability and avoids single points of failure.

---

### **2. End-to-End Encryption**

- **Public/Private Keys and Addresses**:
  - **The uniqueness of sent data is ensured by both the public key and the NPZ address**.
  - Users generate public/private key pairs for secure communication.
  - Public keys are stored in a distributed directory along with NPZ addresses.

- **Message and File Encryption**:
  - Messages and files are encrypted with the recipient's public key.
  - Files are saved as encrypted text files with NPZ identifiers.
  - **Even if a datagram reaches a duplicate NPZ address, it cannot be read due to the incorrect public key**.

- **Key Management**:
  - Users can change their public/private keys at any time.
  - **When keys are changed, all locally stored messages and files are cleared**, ensuring previous data remains inaccessible with new keys.

---

### **3. Client-to-Client Communication**

- **Direct Datagram Transmission**:
  - **Clients send datagrams directly between themselves**, enhancing speed and efficiency.
  - Servers act as routers, facilitating connections and ensuring messages reach their destinations.

- **Efficient Routing**:
  - NPZ's hierarchical addressing allows for optimized routing paths.
  - **Routers cannot read the content of the messages; they only see the recipient's address and public key**.

- **Modified Network Protocols for Routing**:
  - **Routing utilizes modified network protocols**, tailored to the NPZ architecture.
  - These modifications enhance performance, security, and compatibility with NPZ's unique features.

---

### **4. Group Chats**

- **Multiple Recipients**:
  - **Group chats consist of a list of multiple recipients**.
  - **The more recipients, the more datagrams are sent**, each encrypted with a different public key.

- **Message Transmission**:
  - The sender's client sends separate encrypted datagrams for each group member.
  - Each datagram is encrypted with the individual recipient's public key.

- **Merging on the Client Side**:
  - **Messages are merged on the client's side after routing**.
  - The recipient's client reconstructs the group conversation from received messages.

- **Group Name Header**:
  - An **additional header with the group name is included in the encrypted datagram**.
  - This allows the recipient's client to identify and organize messages within the correct group chat.

---

### **5. No Server-Side Storage**

- **Routing Only**:
  - Servers act purely as intermediaries, forwarding encrypted messages and files.
  - No message or file is ever stored on a server.

- **Real-Time Communication**:
  - Messages are routed immediately, ensuring real-time delivery.
  - Offline users receive messages once their client reconnects.

---

### **6. Public Key Distribution and Verification**

- **Distributed Public Key Directory**:
  - Public keys are associated with NPZ addresses and made available in a decentralized directory.

- **Uniqueness Assurance**:
  - **The combination of the NPZ address and public key uniquely identifies a recipient**.
  - This ensures that messages are delivered securely to the intended recipient.

- **Key Verification**:
  - Verification can be done through mutual contacts, certificates, or a web-of-trust system.

---

## **How It Works**

### **1. Sending a Message**

1. **Encrypt the Message**:
   - The sender retrieves the recipient's public key associated with their NPZ address.
   - Encrypts the message or file using the recipient's public key.
   - **The combination of the NPZ address and public key ensures the message is uniquely identified**.

2. **Routing**:
   - The encrypted message is sent as a datagram from the sender's client directly to the recipient's NPZ address.
   - **Servers serve as routers**, verifying the existence of the NPZ address and forwarding the message accordingly.
   - **Routing is performed using modified network protocols**, optimized for NPZ.

3. **Decryption**:
   - The recipient receives the encrypted message.
   - Decrypts the message using their private key.
   - **Even if a datagram reaches a duplicate NPZ address, it cannot be read without the correct private key**.

---

### **2. Group Chats**

1. **Preparing the Message**:
   - The sender composes a message intended for a group chat.
   - Retrieves the public keys of all group members from the public key directory.

2. **Encrypting and Sending**:
   - **For each recipient**, the sender's client:
     - Encrypts the message with the recipient's public key.
     - Includes an **additional header with the group name** in the encrypted datagram.
     - Sends the encrypted datagram to the recipient's NPZ address.

3. **Routing**:
   - Each datagram is routed individually to its recipient.
   - **Servers act as routers**, forwarding the datagrams without storing them.

4. **Receiving and Merging**:
   - Each recipient's client receives the encrypted datagram.
   - Decrypts the message using their private key.
   - **Uses the group name header to place the message in the correct group chat**.
   - **Merging happens on the client side after routing**, reconstructing the group conversation.

---

### **3. Changing Public/Private Keys**

- Users can update their public/private key pairs as needed.
- **Effect of Key Changes**:
  - All locally stored messages and files are cleared.
  - This ensures that previously encrypted data cannot be accessed with the new keys.

---

## **Technical Implementation**

### **1. Addressing and Routing**

- **Hierarchical Addressing**:
  - NPZ's addressing format (`XXX.YYY.ZZZ.VVV`) simplifies routing.

- **Server Verification**:
  - **Servers check if a given NPZ address exists in the specified location** before routing messages.
  - Enhances accuracy and reduces routing errors.

- **Client Datagram Transmission**:
  - **Clients send datagrams directly to each other**, with servers acting as routers to facilitate the connection.

- **Modified Network Protocols**:
  - **Routing uses modified network protocols**, adapted to support NPZ's architecture.
  - These protocols improve routing efficiency and security.

---

### **2. Encryption Workflow**

1. **Generate Key Pairs**:
   - Users create public/private key pairs using algorithms like RSA or ECC.

2. **Encrypt Data**:
   - Messages are encrypted with the recipient's public key.
   - For group chats, separate encryption is performed for each recipient.

3. **Group Name Header**:
   - An additional header containing the group name is included in the encrypted datagram.
   - Ensures that recipients can correctly associate messages with group chats.

4. **Decrypt Data**:
   - The recipient decrypts messages with their private key.
   - **Only the holder of the correct private key can decrypt the message, maintaining confidentiality**.

---

## **Advantages**

- **Privacy**:
  - End-to-end encryption ensures only intended recipients can read messages.
  - **Routers and servers cannot access message content; they only process recipient addresses and public keys**.

- **Security**:
  - Changing public/private keys clears local data, preventing unauthorized access.
  - **Even if a message reaches a duplicate NPZ address, it remains unreadable without the correct private key**.

- **Decentralization**:
  - Users can host their own servers for complete control.
  - Multiple routing paths enhance reliability.

- **Efficiency**:
  - NPZ's hierarchical addressing and client-to-client datagram transmission optimize routing.
  - **Modified network protocols improve routing performance and security**.

- **Scalable Group Chats**:
  - **Group chats are implemented by sending multiple encrypted datagrams**, one for each recipient.
  - **Merging on the client side** ensures messages are organized correctly without burdening the network.

---

## **Getting Started**

1. **Set Up Your Client**:
   - Download the Essa-NPZ client for your platform.
   - Generate your public/private key pair.

2. **Select a Server**:
   - Choose a trusted server or set up your own.

3. **Start Messaging**:
   - Send encrypted messages and files to other users using their NPZ addresses.
   - **Create group chats by selecting multiple recipients**.

---

## **Future Plans**

- **Optimized Group Chat Protocols**:
  - Explore methods to reduce the number of datagrams sent in group chats.
  - Implement broadcast or multicast features within NPZ where feasible.

- **File Sharing Enhancements**:
  - Optimize large file transfers.

- **User-Friendly Key Management**:
  - Implement automated key updates and backups.

- **Mobile Clients**:
  - Develop apps for iOS and Android.

---

## **Contributing**

Essa-NPZ is an open-source project. Contributions are welcome! Here's how you can help:

- Report issues or suggest features in the [Issues](#) section.
- Submit pull requests for code contributions.
- Join discussions to help shape the future of Essa-NPZ.

---

**Disclaimer**: Essa-NPZ is a conceptual application built on the NPZ protocol. While designed for privacy and security, further development and testing are required for production use.

---

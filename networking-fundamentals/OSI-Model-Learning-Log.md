Today, I didn’t just “study networking”… I visualized how data moves layer by layer.

As a cybersecurity learner, I’ve been diving deeper into how data travels from one system to another.
The 𝐎𝐒𝐈 𝐌𝐨𝐝𝐞𝐥 helped me break down something that once felt complex into a simple, structured flow.

𝐇𝐞𝐫𝐞’𝐬 𝐡𝐨𝐰 𝐈 𝐧𝐨𝐰 𝐮𝐧𝐝𝐞𝐫𝐬𝐭𝐚𝐧𝐝 𝐭𝐡𝐞 𝐎𝐒𝐈 𝐌𝐨𝐝𝐞𝐥:

🔹 𝐋𝐚𝐲𝐞𝐫 7 – 𝐀𝐩𝐩𝐥𝐢𝐜𝐚𝐭𝐢𝐨𝐧
This layer is also known as the end-user or desktop layer.
It acts as an interface between the user and the system.

Let’s understand it with an example: we all use Google Chrome in our day-to-day life to search and explore. When you type something, you send a request, and the system processes it in the background. Here, Chrome is the interface because it connects you with the system where you can send or receive data, media, and information.

In simple terms, the Application layer provides the interface through which we interact with the system.

🔹 𝐋𝐚𝐲𝐞𝐫 6 – 𝐏𝐫𝐞𝐬𝐞𝐧𝐭𝐚𝐭𝐢𝐨𝐧
After the message passes from the Application layer, it comes to the Presentation layer. This layer performs three processes:

𝐂𝐨𝐧𝐯𝐞𝐫𝐬𝐢𝐨𝐧 – It converts the message from human-understandable language into machine-understandable format.

𝐄𝐧𝐜𝐫𝐲𝐩𝐭𝐢𝐨𝐧 – It changes the message so only the sender and the receiver can read it. It converts the plantext into ciphertext, this protects the data from unauthorized access.

𝐂𝐨𝐦𝐩𝐫𝐞𝐬𝐬𝐢𝐨𝐧 – It compresses large files or media to make them smaller and save space.

🔹 𝐋𝐚𝐲𝐞𝐫 5 – 𝐒𝐞𝐬𝐬𝐢𝐨𝐧
In the Session layer, the message is handled when the receiver is not available.

First, this layer checks which server is free by sending requests. The server that is available sends back a token. After receiving the token, the Session layer sends the message to that server, where it is stored until the receiver becomes available.

🔹 𝐋𝐚𝐲𝐞𝐫 4 – 𝐓𝐫𝐚𝐧𝐬𝐩𝐨𝐫𝐭
Here, the message goes through two main processes:

𝐒𝐞𝐠𝐦𝐞𝐧𝐭𝐚𝐭𝐢𝐨𝐧 – The message is divided into small units called segments. Each segment contains a sequence number and source and destination port numbers.

𝐅𝐥𝐨𝐰 𝐂𝐨𝐧𝐭𝐫𝐨𝐥 – It controls the flow of data between the sender’s device and the server by adjusting the speed of sending and receiving so both sides stay in sync.

𝐄𝐫𝐫𝐨𝐫 𝐂𝐨𝐧𝐭𝐫𝐨𝐥 – During data transmission( data sending/receiving process), there are chances of data loss or data corruption. This process detects lost or corrupted data and automatically requests the sender to resend it so the message is delivered correctly.

🔹 𝐋𝐚𝐲𝐞𝐫 3 – 𝐍𝐞𝐭𝐰𝐨𝐫𝐤
This layer does two things:

First, it assigns the source and destination IP addresses to each segment. After this, the segments are called 𝐩𝐚𝐜𝐤𝐞𝐭𝐬.
Second, it finds the best possible path for the packets to reach the receiver, since multiple paths can exist between two devices.

🔹𝐋𝐚𝐲𝐞𝐫 2 – 𝐃𝐚𝐭𝐚 𝐋𝐢𝐧𝐤
The Data Link layer adds the sender’s and receiver’s MAC addresses to the data. After this, the packets are called 𝐟𝐫𝐚𝐦𝐞𝐬.

🔹 𝐋𝐚𝐲𝐞𝐫 1 – 𝐏𝐡𝐲𝐬𝐢𝐜𝐚𝐥
The Physical layer converts the message into 0s and 1s (bits) and sends it through the cable, routers, and network devices.

At the receiver’s end, the same process happens in reverse through all seven layers, and finally, the message is delivered to the receiver.

What stood out to me the most was how each layer depends on the one below it — just like in cybersecurity, where one weak point can affect the entire system.

🔗 ## Learning Resources & Links

This learning log includes a short video walkthrough where I explain the OSI Model in my own words and connect each layer to real-world networking and security concepts.

🎥 ## YouTube Video

▶ ## Watch here: https://www.youtube.com/watch?v=Nbda3lVtRro

🔗 ## LinkedIn Post

📌 I’ve also shared this session and key takeaways on LinkedIn:
▶ View post: LinkedIn – https://www.linkedin.com/feed/update/urn:li:ugcPost:7424541947278737408/


If you’re learning networking or cybersecurity too, feel free to explore, connect, or share feedback — I’d love to grow together🚀.


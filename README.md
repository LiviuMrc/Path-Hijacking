# Navigating the Roads of Path Hijacking: Understanding the Risks and Safeguarding Your Journey

In this simple example, we aim to shed light on the mechanics of path hijacking using a straightforward scenario.

Through this illustration, we hope to provide clarity and insight into the dangers posed by path hijacking, empowering users to recognize potential threats and take proactive measures to safeguard their digital journeys. Let's embark on this journey together as we dissect the anatomy of path hijacking and explore strategies to navigate the digital landscape with vigilance and resilience.

## Step 1 Reconnaissance
Login into the machine using user1/letitsnow and assess the situation. 

![image](https://github.com/LiviuMrc/Path-Hijacking/assets/95069685/8e8f5812-0c49-4a08-9ca4-b7ae249e4edf)

And we can notice that we are provided with a setuid binary because it has "s" in the file permissions.

![Screenshot 2024-02-08 212502](https://github.com/LiviuMrc/Path-Hijacking/assets/95069685/cec3f8ad-1f29-43c5-9009-efd338b4c6de)

When we try to execute it we are asked to input either 1 to see the output or 99 to exit the program, it only accepts intigers and overall its not that interesting.

![image](https://github.com/LiviuMrc/Path-Hijacking/assets/95069685/bd4b64d6-a5e1-458c-acc1-315ad5faec36)


If we try to inspect it using "cat" or other file editing commands we can see that the code is obfuscated so the best option is to use "strings".

After inspecting the output we can see that the binary is made in C (uses printf/scanf and is compiled using GCC), but most importantly it uses GNU core utilities: "echo" and "cowsay". Using GNU utilities in setuid binaries can pose security concerns due to potential vulnerabilities and security risks associated with the implementation and behavior of these utilities, in this case it will be exploited to grant Privilege Escalation.

![ss2](https://github.com/LiviuMrc/Path-Hijacking/assets/95069685/bb707ad5-0c98-4de4-ad39-ad0bd8786894)



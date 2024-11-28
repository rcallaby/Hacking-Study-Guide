# Android Focused Technical Interview Questions

---

## **General Android Security Knowledge**
1. **Q: What are the key components of the Android architecture?**
   - **Answer:**
     - **Linux Kernel**: Core system functions, security features (SELinux), and hardware interaction.
     - **Hardware Abstraction Layer (HAL)**: Interface between the hardware and Android framework.
     - **Android Runtime (ART)**: Runs apps and manages memory.
     - **Application Framework**: Manages UI, activities, and app resources.
     - **Applications**: User-facing apps.

2. **Q: How does Android enforce application sandboxing?**
   - **Answer:**
     - Each app runs in its own process and is assigned a unique user ID (UID).
     - Apps cannot access other apps' data without explicit permissions.
     - SELinux policies enforce Mandatory Access Control (MAC).

3. **Q: Explain the Android permission model.**
   - **Answer:**
     - Permissions are declared in the app's `AndroidManifest.xml`.
     - Users grant permissions at runtime for dangerous permissions (e.g., camera, location).
     - Normal permissions are automatically granted (e.g., Internet).

4. **Q: What is Google Play Protect, and how does it contribute to Android security?**
   - **Answer:**
     - Google Play Protect is a security service that scans apps for malware before and after installation.
     - It uses machine learning to detect harmful behavior.
     - It also helps identify potentially harmful apps (PHAs) and warns users.

---

## **Mobile Penetration Testing Basics**
5. **Q: What tools would you use to analyze Android applications for security vulnerabilities?**
   - **Answer:**
     - Static Analysis: **APKTool, jadx, MobSF, Androguard**.
     - Dynamic Analysis: **Frida, Xposed Framework, Drozer, Genymotion, Burp Suite**.
     - Vulnerability Scanning: **qark, Mobile Security Framework (MobSF)**.

6. **Q: How do you reverse engineer an Android APK?**
   - **Answer:**
     - Decompile APK using **APKTool** to extract resources and manifest.
     - Use **jadx** or **jd-gui** to analyze Java code.
     - Examine native libraries using tools like **Ghidra**.

7. **Q: Describe the process of performing dynamic analysis on an Android app.**
   - **Answer:**
     - Set up a virtual Android device (e.g., Genymotion or AVD).
     - Install the app and monitor traffic using **Burp Suite** or **mitmproxy**.
     - Hook into app functions using **Frida** or **Xposed Framework**.
     - Test for runtime behaviors, such as API calls, permissions abuse, or sensitive data exposure.

8. **Q: What is the purpose of a mobile app proxy in penetration testing, and how do you configure one?**
   - **Answer:**
     - A proxy intercepts and inspects app traffic.
     - To configure:
       1. Set the proxy server in the device's network settings.
       2. Install the proxy's SSL certificate (e.g., Burp CA) on the device.
       3. Ensure the app uses HTTP/HTTPS for traffic.

---

## **Exploiting Android Vulnerabilities**
9. **Q: How would you test an app for insecure data storage?**
   - **Answer:**
     - Look for sensitive data stored in plaintext in:
       - Internal storage (`/data/data/[package_name]`).
       - SharedPreferences.
       - SQLite databases.
     - Use tools like **adb** or **MobSF** to inspect file contents.

10. **Q: What are common Android vulnerabilities, and how would you exploit them?**
    - **Answer:**
      - **Insecure Data Storage**: Examine app files and logs for sensitive data.
      - **Insecure Communication**: Intercept network traffic using Burp Suite.
      - **Weak Authentication**: Brute-force login APIs or bypass mechanisms.
      - **Exposed Components**: Exploit exported activities or broadcast receivers.

11. **Q: How would you bypass root detection mechanisms in an Android app?**
    - **Answer:**
      - Modify the app's smali code to remove detection logic.
      - Use **Frida** to hook and override root-checking methods dynamically.

---

## **Advanced Topics**
12. **Q: How would you perform a memory dump of a running Android application?**
    - **Answer:**
      - Use tools like **Frida**, **gdb**, or **volatility** for live analysis.
      - Analyze native libraries or decrypted content from memory.

13. **Q: How can you test an Android app for improper SSL/TLS validation?**
    - **Answer:**
      - Use a proxy like Burp Suite to test if the app accepts invalid certificates.
      - Check if the app uses `HostnameVerifier` or `TrustManager` implementations with known flaws.

14. **Q: Explain the OWASP Mobile Top 10 and their relevance to Android.**
    - **Answer:**
      - Covers vulnerabilities like **M1: Improper Platform Usage**, **M2: Insecure Data Storage**, and **M9: Reverse Engineering**.
      - Specific to Android, these could involve misuse of permissions, improper key storage, or exposing code through APKs.

---

## **Hands-On Scenarios**
15. **Q: You are tasked with finding hardcoded API keys in an Android app. How do you proceed?**
    - **Answer:**
      - Decompile the APK using APKTool or jadx.
      - Search for strings like `API_KEY` or endpoints in the smali or Java code.
      - Inspect the `res/values/strings.xml` file.

16. **Q: How would you test for insecure communication in an app that uses HTTPS?**
    - **Answer:**
      - Configure a proxy (Burp Suite) and set up certificate pinning bypass (e.g., using Frida scripts).
      - Analyze network traffic for sensitive data transmitted insecurely.

17. **Q: How do you identify and exploit vulnerable exported activities?**
    - **Answer:**
      - Use `adb` commands or Drozer to list exported activities.
      - Attempt unauthorized access or input injection into these activities.

---

## **Behavioral/Practical Questions**
18. **Q: Describe a challenging Android pentest engagement and how you overcame obstacles.**
    - **Tip**: Highlight a specific instance, the problem (e.g., SSL pinning), the tools/techniques used, and the outcome.

19. **Q: How do you stay updated with Android penetration testing techniques?**
    - **Answer:**
      - Follow security blogs (e.g., Google Security Blog, Android Security).
      - Participate in CTFs and review write-ups.
      - Explore open-source tools and frameworks.

20. **Q: Can you explain the concept of privilege escalation on Android devices?**
    - **Answer:**
      - Privilege escalation involves exploiting flaws to gain elevated rights.
      - Use exploits targeting vulnerabilities in the kernel or app sandbox.

---
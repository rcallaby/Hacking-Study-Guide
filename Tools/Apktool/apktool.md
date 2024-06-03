# Apktool

### Step 1: Setup Environment

#### Install Java
Apktool requires Java. Ensure you have Java installed on your system.
```bash
java -version
```
If not installed, download and install from [Java SE Downloads](https://www.oracle.com/java/technologies/javase-downloads.html).

#### Download Apktool
Download Apktool from its official repository:
1. **Apktool JAR**: [Apktool JAR](https://bitbucket.org/iBotPeaches/apktool/downloads/)
2. **Apktool Script**: [Apktool Script](https://raw.githubusercontent.com/iBotPeaches/Apktool/master/scripts/linux/apktool)

Place both files in a directory and make the script executable:
```bash
chmod +x apktool
```

### Step 2: Decompile an APK
Decompiling an APK extracts the resources and disassembles the classes.dex file to Smali code.

```bash
./apktool d <path_to_apk>
```
Example:
```bash
./apktool d app-release.apk
```
This command creates a directory named `app-release`, containing the decompiled resources and Smali code.

### Step 3: Analyze Decompiled Code
After decompiling, you can inspect the contents:

- **Smali Code**: Located in the `smali/` directory. Smali is a readable representation of the Dalvik bytecode.
- **Resources**: Found in `res/` directory. These include layouts, strings, and other XML files.

As a penetration tester, focus on:
- **AndroidManifest.xml**: Check for exported activities, services, and receivers.
- **Network Security Config**: Look for cleartext traffic, SSL configurations.
- **Hardcoded Values**: Secrets, API keys, credentials in Smali code or resources.

### Step 4: Modify the APK
You may want to modify the APK to test certain aspects of its functionality.

1. **Make Changes**: Edit the Smali code or resource files as required.
2. **Rebuild the APK**: Use Apktool to recompile the APK.
   ```bash
   ./apktool b <decompiled_directory>
   ```
   Example:
   ```bash
   ./apktool b app-release
   ```

### Step 5: Sign the APK
Rebuilt APKs need to be signed before they can be installed on a device.

1. **Generate a Keystore** (if you don't have one):
   ```bash
   keytool -genkey -v -keystore my-release-key.keystore -alias alias_name -keyalg RSA -keysize 2048 -validity 10000
   ```
2. **Sign the APK**:
   ```bash
   jarsigner -verbose -sigalg SHA1withRSA -digestalg SHA1 -keystore my-release-key.keystore <path_to_apk> alias_name
   ```
3. **Verify the APK**:
   ```bash
   jarsigner -verify <path_to_apk>
   ```

### Step 6: Install the APK
Finally, install the APK on your device or emulator for testing.

```bash
adb install <path_to_apk>
```

### Example Workflow
1. **Decompile APK**:
   ```bash
   ./apktool d app-release.apk
   ```
2. **Modify Smali Code**:
   - Edit files in `app-release/smali/`
3. **Rebuild APK**:
   ```bash
   ./apktool b app-release
   ```
4. **Sign APK**:
   ```bash
   jarsigner -verbose -sigalg SHA1withRSA -digestalg SHA1 -keystore my-release-key.keystore app-release/dist/app-release.apk alias_name
   ```
5. **Install APK**:
   ```bash
   adb install app-release/dist/app-release.apk
   ```

### Additional Tips for Penetration Testing
- **Automate Analysis**: Use scripts to automate decompiling, searching for known vulnerabilities, and repackaging APKs.
- **Dynamic Analysis**: Combine Apktool with tools like Frida for runtime manipulation and inspection.
- **Static Analysis**: Use complementary tools like MobSF for comprehensive static analysis.

By following this guide, you can effectively use Apktool to dissect and analyze Android applications, identify security flaws, and test potential vulnerabilities.
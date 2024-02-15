# Atomic Notes Project
- 📫 You can reach me from email: DevBehindYou@gmail.com
- Ongoing Project.
- source code will available soon.
__________________________________________________________________
![image](https://github.com/DevBehindYou/Atomic-Notes-Project/assets/147663456/a6519e43-0e3e-4ce6-aebe-d508a1aadf97)

All you need is a simple yet effective note-taking application

#No Tracking
#No Data Thefting
#No Permission Required
#Your Data, Your control

- Atomic Notes come with offline and online cloud storage synchronization.
- Will provide encryption over personal data and real-time cloud sync.
- Will give the user total control over their personal data.
- Come with offline local storage, so you can access your notes at any time without an internet connection.
- For the safety of notes, cloud backup is available in the application with a fast cloud sync function. 
- The application is packed with a beautiful UI and user-friendly design.
- Optimized and power-full.
![20240215_162548 (1)](https://github.com/DevBehindYou/Atomic-Notes-Project/assets/147663456/82a66baf-8332-4b2a-b1e4-6825f1e06bf1)

# Roadmap:

- Play Store Launch:

Aim to launch the app on the Google Play Store to reach a wider audience.
Follow platform-specific guidelines for app submission and optimization.

- Platform Independence:

Develop web, iOS, Android, and Windows versions of the app to cater to diverse user preferences.
Ensure consistent features and user experience across all platforms.
Leverage cross-platform development frameworks like Flutter or React Native for efficient development.

# Known Issues:

- Sync Errors:

Sync errors may occur due to unstable internet connections.
Manual sync option available to mitigate automatic sync failures.

- Biometric Authentication:

Biometric authentication enhances security but may encounter issues on unsupported devices or versions.
Removing device lock can lead to app instability or crashes, especially on older Android versions.

- Multiple Password Attempts:

Non-biometric devices, particularly pre-Android 9 versions, may be vulnerable to multiple password attempts.
Consider implementing additional security measures or limiting login attempts to mitigate risks.

# Troubleshooting:
- App Stability:

App crashes are minimized, but if encountered, ensure the latest version is installed.
If crashes persist, provide device details and steps to reproduce for support.

- Sync Errors:

Unstable internet connections may lead to sync errors. Verify network stability.
Manually trigger sync if automatic sync fails to resolve temporary network issues.

- Biometric Authentication:

Biometric authentication enhances security. Ensure device and app support.
If authentication issues arise, re-enroll biometric data and verify app permissions.

- Device Lock Removal:

Removing device lock can cause app instability or crashes. Recommend keeping it enabled.
If instability occurs after lock removal, consider re-enabling it or contacting support.

- Multiple Password Attempts:

Implement security measures to prevent brute-force attacks on non-biometric devices.
Educate users on password strength and recommend enabling device lock for added security.

# System Requirements:

Operating System: Android, ios comming soon 
Minimum SDK Level: 23 (Android 6.0, Marshmallow)
Recommended SDK Level: 32 (Android 12, S)
Hardware: arm64v8 or armv7, Compatible with devices running Android 6.0 or later

# Dependencies:

flutter_lints dbms google_nav_bar hive hive_flutter lutter_slidable flutter_svg provider flutter_staggered_grid_view connectivity_plus smooth_page_indicator cupertino_icons local_auth encrypt

# AES encryption

Uint8List encryptMessage(Uint8List key, Uint8List iv, String message) {

  final plaintext = Uint8List.fromList(utf8.encode(message));
  
  final paddedPlaintext = padPlaintext(plaintext);

  final cipher = CBCBlockCipher(AESFastEngine())
    ..init(
      true,
      ParametersWithIV(KeyParameter(key), iv),
    );

  return cipher.process(Uint8List.fromList(paddedPlaintext));
}

Uint8List padPlaintext(Uint8List plaintext) {

  final blockSize = 16;
  final paddedLength = blockSize * ((plaintext.length + blockSize - 1) ~/ blockSize);
  final paddingLength = paddedLength - plaintext.length;
  final paddedPlaintext = Uint8List(paddedLength)..setAll(0, plaintext);
  paddedPlaintext.fillRange(plaintext.length, paddedLength, paddingLength);
  return paddedPlaintext;
}

void main() {

  final key = Uint8List.fromList(utf8.encode('your_secret_key_here'));
  final iv = Uint8List(16); // Initialization Vector
  final message = 'your_note_here';

  final encryptedMessage = encryptMessage(key, iv, message);
  print('Encrypted message: ${base64.encode(encryptedMessage)}');
}







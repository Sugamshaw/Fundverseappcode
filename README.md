# 💰 Fund Verse - Fund Management System

<div align="center">
  <img src="https://raw.githubusercontent.com/Sugamshaw/Fundverseappcode/master/app/src/main/res/drawable/app_logo.png" alt="Fund Verse Logo" width="240"/>

  
  [![Android](https://img.shields.io/badge/Platform-Android-green.svg)](https://www.android.com/)
  [![Kotlin](https://img.shields.io/badge/Language-Kotlin-blue.svg)](https://kotlinlang.org/)
  [![API](https://img.shields.io/badge/API-24%2B-brightgreen.svg)](https://android-arsenal.com/api?level=24)
  [![License](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
</div>

## 📖 Overview

**Fund Verse** is a comprehensive Android application designed for efficient fund management. It provides a complete solution for managing legal entities, management entities, funds, sub-funds, and share classes with an intuitive and modern user interface.

## ✨ Features

### 🏢 Entity Management
- **Legal Entities**: Manage legal entity information including LEI, jurisdiction, and entity type
- **Management Entities**: Track management entities with registration numbers and domicile information
- **Real-time CRUD Operations**: Create, Read, Update, and Delete operations with instant synchronization

### 💼 Fund Management
- **Fund Master**: Complete fund information management with ISIN, base currency, and status tracking
- **Sub-Funds**: Hierarchical fund structure support with parent-child relationships
- **Share Classes**: Detailed share class management including NAV, AUM, fees, and performance metrics

### 🔍 Advanced Features
- **Smart Search**: Real-time search across all entities with instant filtering
- **Cross-Navigation**: Seamless navigation between related entities (Legal → Management → Funds → Sub-Funds → Share Classes)
- **Filter System**: Dynamic filtering with visual filter banners and easy clearing
- **Swipe-to-Refresh**: Pull-down to refresh data across all screens
- **Sort Functionality**: Sort share classes by AUM, NAV, and Management Fee
- **Empty States**: Helpful empty state screens with action prompts

### 🎨 Modern UI/UX
- **Material Design 3**: Latest Material Design components and guidelines
- **Collapsible Search**: Search bars that collapse on scroll for more viewing space
- **Extended FAB**: Context-aware floating action buttons that shrink/extend on scroll
- **Smooth Animations**: Polished transitions and animations throughout
- **Dark/Light Theme Support**: (Coming soon)

### 🔐 Authentication & Security
- **Firebase Authentication**: Secure email/password authentication
- **User Profile Management**: Account settings and profile customization
- **Session Management**: Automatic session handling with secure logout
- **Password Reset**: Email-based password recovery
- **Account Deletion**: Complete account deletion with data cleanup

## 🏗️ Architecture

### Design Pattern
- **MVVM Architecture**: Clear separation of concerns
- **Repository Pattern**: Centralized data management
- **Single Activity**: Modern single-activity architecture with fragments

### Tech Stack

#### Core
- **Language**: Kotlin 100%
- **Min SDK**: 24 (Android 7.0)
- **Target SDK**: 34 (Android 14)
- **Compile SDK**: 34

#### UI/UX
- **View Binding**: Type-safe view access
- **Material Design 3**: Latest material components
- **RecyclerView**: Efficient list rendering with DiffUtil
- **CoordinatorLayout**: Advanced scrolling behaviors
- **CollapsingToolbarLayout**: Collapsible app bars
- **SwipeRefreshLayout**: Pull-to-refresh functionality

#### Networking
- **Retrofit 2**: REST API communication
- **Gson**: JSON serialization/deserialization
- **OkHttp**: HTTP client with logging interceptor

#### Backend & Database
- **Firebase Authentication**: User authentication
- **Firebase Firestore**: Cloud database for user data
- **RESTful API**: Custom backend API for fund data

#### Dependency Injection
- Manual dependency injection with RetrofitClient singleton

#### Asynchronous Programming
- **Kotlin Coroutines**: Async operations
- **Lifecycle Scope**: Lifecycle-aware coroutines

## 📱 App Structure
```
com.example.fundbank/
├── adapters/           # RecyclerView adapters
├── api/               # Retrofit API interfaces
├── fragments/         # UI fragments
├── models/           # Data models
├── activities/       # Activities (Main, Login, Settings, etc.)
└── utils/            # Utility classes
```

## 🔧 Setup & Installation

### Prerequisites
- Android Studio Hedgehog or later
- JDK 17 or higher
- Android SDK 24+
- Gradle 8.0+

### Installation Steps

1. **Clone the Repository**
```bash
   git clone https://github.com/Sugamshaw/Fundverseappcode.git
   cd fundverse
```

2. **Configure Firebase**
   - Create a Firebase project at [Firebase Console](https://console.firebase.google.com/)
   - Enable Email/Password Authentication
   - Enable Firestore Database
   - Download `google-services.json` and place it in the `app/` directory

3. **Configure API Endpoint**
   - Open `api/RetrofitClient.kt`
   - Update the `BASE_URL` with your backend API URL:
```kotlin
     private const val BASE_URL = "http://your-api-url:8080/"
```

4. **Build the Project**
```bash
   ./gradlew clean build
```

5. **Run the App**
   - Connect an Android device or start an emulator
   - Click "Run" in Android Studio or use:
```bash
     ./gradlew installDebug
```

## 🔐 Security Considerations

### Authentication Security
- ✅ Firebase Authentication with secure email/password handling
- ✅ No passwords stored locally
- ✅ Session tokens managed by Firebase SDK
- ✅ Automatic session expiration and refresh

### Data Security
- ✅ HTTPS/TLS for all API communications
- ✅ Firebase Security Rules for Firestore access control
- ✅ User data isolation - users can only access their own data
- ✅ Secure password reset flow via email

### Best Practices Implemented
- ✅ No hardcoded secrets or API keys in source code
- ✅ ProGuard/R8 code obfuscation enabled for release builds
- ✅ Certificate pinning (recommended for production)
- ✅ Input validation on all user inputs
- ✅ SQL injection prevention through Retrofit + Gson

### Recommended Security Enhancements for Production
1. **API Key Management**: Use BuildConfig or environment variables for API keys
2. **Certificate Pinning**: Implement SSL certificate pinning in OkHttp
3. **Biometric Authentication**: Add fingerprint/face unlock option
4. **Encrypted Local Storage**: Use EncryptedSharedPreferences for sensitive data
5. **Rate Limiting**: Implement request rate limiting on backend
6. **2FA**: Two-factor authentication support

### Firebase Security Rules Example
```javascript
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /users/{userId} {
      allow read, write: if request.auth != null && request.auth.uid == userId;
    }
  }
}
```

## 🌐 API Endpoints

### Legal Entities
- `GET /api/legalentities` - Get all legal entities
- `POST /api/legalentities` - Create legal entity
- `PUT /api/legalentities/{id}` - Update legal entity
- `DELETE /api/legalentities/{id}` - Delete legal entity

### Management Entities
- `GET /api/managemententities` - Get all management entities
- `POST /api/managemententities` - Create management entity
- `PUT /api/managemententities/{id}` - Update management entity

### Funds
- `GET /api/funds` - Get all funds
- `POST /api/funds` - Create fund
- `PUT /api/funds/{id}` - Update fund

### Sub-Funds
- `GET /api/subfunds` - Get all sub-funds
- `POST /api/subfunds` - Create sub-fund
- `PUT /api/subfunds/{id}` - Update sub-fund

### Share Classes
- `GET /api/shareclasses` - Get all share classes
- `POST /api/shareclasses` - Create share class
- `PUT /api/shareclasses/{id}` - Update share class

## 🐛 Troubleshooting

### Common Issues

**Issue: Firebase Authentication not working**
- Solution: Ensure `google-services.json` is in the correct location
- Verify Firebase project configuration

**Issue: API connection failed**
- Solution: Check BASE_URL in RetrofitClient.kt
- Ensure backend server is running
- Verify network permissions in AndroidManifest.xml

**Issue: App crashes on startup**
- Solution: Check Logcat for stack trace
- Verify all dependencies are properly synced
- Clear app data and cache

## 📊 Performance Optimizations

- ✅ **RecyclerView ViewHolder Pattern**: Efficient list rendering
- ✅ **DiffUtil**: Smart list updates with minimal UI refreshes
- ✅ **Coroutines**: Non-blocking asynchronous operations
- ✅ **ViewBinding**: No findViewById overhead
- ✅ **Lifecycle-Aware Components**: Prevents memory leaks
- ✅ **Image Optimization**: (Add image loading library like Glide/Coil if needed)

## 🎯 Roadmap

### Upcoming Features
- [ ] Dark theme support
- [ ] Offline mode with local caching
- [ ] Data export (PDF/Excel)
- [ ] Advanced charts and analytics
- [ ] Multi-language support
- [ ] Biometric authentication
- [ ] Push notifications
- [ ] Widget support
- [ ] Tablet optimization

## 📄 License
```
MIT License

Copyright (c) 2025 Fund Verse

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

## 👥 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

### Coding Standards
- Follow Kotlin coding conventions
- Use meaningful variable and function names
- Add comments for complex logic
- Write unit tests for new features
- Update documentation as needed

## 📞 Support & Contact

- **Email**: support@fundverse.com
- **Issues**: [GitHub Issues](/issues)
- **Documentation**: [Wiki](https://github.com/Sugamshaw/Fundverseappcode/wiki)

## 🙏 Acknowledgments

- [Material Design](https://material.io/design) for design guidelines
- [Firebase](https://firebase.google.com/) for authentication and database
- [Retrofit](https://square.github.io/retrofit/) for networking
- [Kotlin Coroutines](https://kotlinlang.org/docs/coroutines-overview.html) for async programming

---

## 🔧 Advanced Troubleshooting - Gradle & Build Issues

### ⚠️ Critical: Kotlin Plugin Already Registered Error

If you encounter the error:
```
Plugin with id 'kotlin-android' already registered
```

This is a **persistent cache issue** where the Kotlin plugin is being registered twice in your Gradle configuration. Follow this complete nuclear cleanup process:

---

### 🗑️ Step 1: Close Android Studio Completely

**IMPORTANT**: Fully close Android Studio before proceeding. Don't just close the project window.

- **Windows**: Right-click Android Studio in taskbar and click "Close all windows"
- **macOS**: Cmd+Q to quit
- **Linux**: Close all Android Studio windows
- **Verify**: Check Task Manager/Activity Monitor to ensure no Android Studio processes are running

---

### 🧹 Step 2: Manual Cleanup (Critical!)

#### A. In Your Project Root Directory

Navigate to your project folder:
```
Windows: C:\Users\YOUR_USERNAME\AndroidStudioProjects\Fundbank\
macOS/Linux: ~/AndroidStudioProjects/Fundbank/
```

**Delete the following folders and files:**
```
📁 Project Root/
├── 🗑️ .gradle/          ← DELETE THIS FOLDER
├── 🗑️ .idea/            ← DELETE THIS FOLDER
├── 🗑️ build/            ← DELETE THIS FOLDER
├── 📁 app/
│   └── 🗑️ build/        ← DELETE THIS FOLDER
└── 🗑️ local.properties  ← DELETE THIS FILE
```

**Commands (Optional - Use Terminal/Command Prompt):**

**Windows (PowerShell):**
```powershell
cd C:\Users\YOUR_USERNAME\AndroidStudioProjects\Fundbank
Remove-Item -Recurse -Force .gradle
Remove-Item -Recurse -Force .idea
Remove-Item -Recurse -Force build
Remove-Item -Recurse -Force app\build
Remove-Item -Force local.properties
```

**macOS/Linux (Terminal):**
```bash
cd ~/AndroidStudioProjects/Fundbank
rm -rf .gradle .idea build app/build local.properties
```

---

#### B. In Gradle Home Directory

Navigate to your Gradle home folder:
```
Windows: C:\Users\YOUR_USERNAME\.gradle\
macOS/Linux: ~/.gradle/
```

**Delete the following folders:**
```
📁 .gradle/
├── 🗑️ caches/    ← DELETE THIS FOLDER
└── 🗑️ daemon/    ← DELETE THIS FOLDER
```

**Commands:**

**Windows (PowerShell):**
```powershell
cd C:\Users\YOUR_USERNAME\.gradle
Remove-Item -Recurse -Force caches
Remove-Item -Recurse -Force daemon
```

**macOS/Linux (Terminal):**
```bash
cd ~/.gradle
rm -rf caches daemon
```

---

#### C. Android Studio Cache (Optional but Recommended)

**Windows:**
```
C:\Users\YOUR_USERNAME\AppData\Local\Google\AndroidStudio*
```
Navigate to this folder and delete the `caches` folder inside.

**macOS:**
```
~/Library/Caches/Google/AndroidStudio*
```
Delete the cache folders.

**Linux:**
```
~/.cache/Google/AndroidStudio*
```
Delete the cache folders.

**OR use Android Studio's built-in cache cleaner (if you can open AS):**
1. File → Invalidate Caches / Restart
2. Select "Invalidate and Restart"

---

### ✅ Step 3: Verify Files Are Clean

**Checklist before reopening Android Studio:**
- [ ] `.gradle` folder deleted from project root
- [ ] `.idea` folder deleted from project root
- [ ] `build` folders deleted (root and app)
- [ ] `local.properties` deleted
- [ ] `caches` folder deleted from `~/.gradle/`
- [ ] `daemon` folder deleted from `~/.gradle/`
- [ ] Android Studio completely closed

---

### 🔄 Step 4: Reopen and Rebuild

1. **Reopen Android Studio**
   - Open your project from scratch
   - Let Android Studio re-index completely (wait for the progress bar at bottom)

2. **Gradle Sync**
   - Android Studio will automatically trigger Gradle sync
   - If not, click: **File → Sync Project with Gradle Files**

3. **Clean Build**
```bash
   ./gradlew clean
```

4. **Rebuild with Refresh**
```bash
   ./gradlew build --refresh-dependencies
```

5. **Run the App**
   - Try running the app now
   - If still issues persist, continue to Step 5

---

### 🔍 Step 5: Additional Diagnostics

If the problem persists after complete cleanup:

#### Check build.gradle Files

**Project-level build.gradle:**
```gradle
// ❌ Make sure kotlin plugin is NOT applied here
plugins {
    id 'com.android.application' version '8.x.x' apply false
    id 'com.android.library' version '8.x.x' apply false
    id 'org.jetbrains.kotlin.android' version '1.9.x' apply false // ✅ Only declare, don't apply
}
```

**App-level build.gradle:**
```gradle
// ✅ Apply kotlin plugin ONLY here
plugins {
    id 'com.android.application'
    id 'org.jetbrains.kotlin.android'
    id 'com.google.gms.google-services'
}
```

#### Verify No Duplicate Plugin Applications

Search your entire project for:
```gradle
apply plugin: 'kotlin-android'
```

**Should appear ONLY ONCE** in `app/build.gradle` (and preferably use the `plugins {}` block instead).

---

### 🚨 Nuclear Option: Complete Fresh Start

If all else fails:

1. **Backup your source code**
   - Copy `app/src/` folder
   - Copy any custom configurations

2. **Create a new project**
   - Create new Android project in Android Studio
   - Copy your backed-up source files
   - Reconfigure dependencies

3. **Fresh Gradle setup**
   - Use the new project's Gradle configuration
   - Gradually add your dependencies back

---

### 💡 Prevention Tips

To avoid this issue in the future:

1. **Don't manually edit `.gradle` files** unless necessary
2. **Use "Invalidate Caches" regularly**: File → Invalidate Caches / Restart
3. **Update Gradle/Plugin versions carefully**: Test in a branch first
4. **Keep Android Studio updated**: Latest stable version has better cache management
5. **Use version catalogs** for dependency management (Gradle 7.0+)

---

### 📋 Quick Reference Commands

**Windows PowerShell (Run as Administrator):**
```powershell
# Navigate to project
cd C:\Users\YOUR_USERNAME\AndroidStudioProjects\Fundbank

# Clean project
Remove-Item -Recurse -Force .gradle, .idea, build, app\build -ErrorAction SilentlyContinue
Remove-Item -Force local.properties -ErrorAction SilentlyContinue

# Clean Gradle home
cd C:\Users\YOUR_USERNAME\.gradle
Remove-Item -Recurse -Force caches, daemon -ErrorAction SilentlyContinue

# Return to project
cd C:\Users\YOUR_USERNAME\AndroidStudioProjects\Fundbank

# After reopening Android Studio
.\gradlew clean build --refresh-dependencies
```

**macOS/Linux Terminal:**
```bash
# Navigate to project
cd ~/AndroidStudioProjects/Fundbank

# Clean project
rm -rf .gradle .idea build app/build local.properties

# Clean Gradle home
rm -rf ~/.gradle/caches ~/.gradle/daemon

# After reopening Android Studio
./gradlew clean build --refresh-dependencies
```

---

### 🆘 Still Having Issues?

If you've followed all steps and still experiencing problems:

1. **Check Android Studio Version**: Update to the latest stable
2. **Check JDK Version**: Ensure you're using JDK 17
3. **Check Gradle Version**: Verify compatibility with your Android Studio version
4. **Check for Antivirus Interference**: Some antivirus software blocks Gradle operations
5. **Check Disk Space**: Ensure you have at least 10GB free space
6. **Network Issues**: Try downloading dependencies with VPN/proxy if in restricted regions

**Open an Issue:**
- Include your Android Studio version
- Include your Gradle version
- Include complete error log from "Build" tab
- Mention which cleanup steps you've already tried

---

### 📚 Useful Links

- [Android Studio Cache Management](https://developer.android.com/studio/intro/studio-config#file_location)
- [Gradle Build Cache](https://docs.gradle.org/current/userguide/build_cache.html)
- [Kotlin Gradle Plugin Documentation](https://kotlinlang.org/docs/gradle.html)
- [Android Gradle Plugin Release Notes](https://developer.android.com/studio/releases/gradle-plugin)

---

<div align="center">
  Made with ❤️ by Fund Verse Team
  
  ⭐ Star us on GitHub — it helps!
  
  **Having issues? Don't hesitate to open an [Issue](https://github.com/Sugamshaw/Fundverseappcode/issues)!**
</div>

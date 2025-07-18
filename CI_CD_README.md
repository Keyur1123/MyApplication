# Android CI/CD Pipeline

This project includes a comprehensive CI/CD pipeline for building and testing Android applications using GitHub Actions.

## 🚀 Features

- **Multi-Build Support**: Builds both debug and release APKs
- **Automated Testing**: Unit tests, instrumented tests, and lint checks
- **Security Scanning**: Dependency vulnerability checks
- **Artifact Management**: Automatic upload of APKs and reports
- **Caching**: Optimized Gradle and dependency caching
- **Manual Triggers**: Support for manual workflow execution

## 📋 Workflow Jobs

### 1. Build Job
- **Purpose**: Compiles the Android application
- **Triggers**: Push to main/develop, PRs, manual dispatch
- **Outputs**: Debug and Release APKs, build reports

### 2. Test Job
- **Purpose**: Runs instrumented tests
- **Dependencies**: Requires build job completion
- **Outputs**: Test reports

### 3. Lint Job
- **Purpose**: Code quality and style checks
- **Outputs**: Lint reports

### 4. Security Job
- **Purpose**: Dependency vulnerability scanning
- **Outputs**: Security reports

## 🔧 Usage

### Automatic Triggers
The workflow automatically runs on:
- Push to `main` or `develop` branches
- Pull requests to `main` or `develop` branches

### Manual Execution
1. Go to GitHub Actions tab
2. Select "Android CI/CD" workflow
3. Click "Run workflow"
4. Choose build type (debug/release)
5. Click "Run workflow"

## 📁 Artifacts

The workflow generates the following artifacts:

### APK Files
- `app-debug`: Debug version APK (30 days retention)
- `app-release`: Release version APK (30 days retention)

### Reports
- `build-reports`: Build output and reports (7 days retention)
- `test-reports`: Test execution reports (7 days retention)
- `lint-reports`: Code quality reports (7 days retention)
- `security-reports`: Security scan reports (7 days retention)

## ⚙️ Configuration

### Build Types
- **Debug**: 
  - Application ID suffix: `.debug`
  - Version name suffix: `-debug`
  - Debuggable: true
  - Minification: disabled

- **Release**:
  - Minification: enabled
  - Resource shrinking: enabled
  - ProGuard optimization: enabled

### Environment Variables
- `GRADLE_OPTS`: Optimized JVM settings for faster builds
- Java version: 11 (Temurin distribution)
- Android SDK: Latest stable version

## 🔍 Monitoring

### Build Status
Monitor build status in the GitHub Actions tab:
- ✅ Green: All jobs passed
- ❌ Red: One or more jobs failed
- 🟡 Yellow: Jobs in progress

### Performance Metrics
- Build time optimization through caching
- Parallel job execution
- Gradle build scan integration

## 🛠️ Troubleshooting

### Common Issues

1. **Build Failures**
   - Check Gradle wrapper validation
   - Verify Java version compatibility
   - Review dependency conflicts

2. **Test Failures**
   - Ensure all tests pass locally
   - Check for flaky tests
   - Review test environment setup

3. **Lint Errors**
   - Fix code style issues
   - Address deprecated API usage
   - Resolve resource conflicts

### Debug Steps
1. Check workflow logs in GitHub Actions
2. Download and review artifact reports
3. Run commands locally to reproduce issues
4. Check Gradle build scan for detailed analysis

## 📈 Best Practices

1. **Keep Dependencies Updated**: Regularly update Gradle and library versions
2. **Monitor Build Times**: Use build scans to identify bottlenecks
3. **Review Security Reports**: Address vulnerability findings promptly
4. **Test Coverage**: Maintain good test coverage for critical paths
5. **Code Quality**: Fix lint warnings and errors regularly

## 🔐 Security Considerations

- Debug builds use debug signing for CI/CD
- Release builds should use proper signing in production
- Security scans run on all dependencies
- Sensitive data should not be committed to repository

## 📞 Support

For issues with the CI/CD pipeline:
1. Check the workflow logs
2. Review this documentation
3. Create an issue with detailed error information
4. Include relevant logs and error messages 
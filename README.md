
# Jenkins CI/CD Pipeline – Maven, Nexus & Tomcat Deployment

## Project Overview

This project demonstrates an automated CI/CD pipeline using Jenkins, Maven, Nexus Repository Manager, and Apache Tomcat.

The pipeline retrieves source code from GitHub, builds the application using Maven, and deploys the generated WAR file to a remote Tomcat server.

## Tools & Technologies

- **Git & GitHub** – Source code management
- **Jenkins** – CI/CD automation
- **Maven** – Build and deployment management
- **Nexus Repository Manager** – Artifact repository
- **Apache Tomcat 9** – Application server
- **Linux (Amazon EC2)** – Server environment

## CI/CD Workflow

```text
Developer
    |
    v
  GitHub
    |
    v
  Jenkins
    |
    v
 Maven Build
    |
    v
 Generate WAR File
    |
    v
 Nexus Repository
    |
    v
 Tomcat Deployment
    |
    v
 Running Web Application
```

## Project Implementation

### 1. GitHub Integration
- Created a GitHub repository to store application source code.
- Configured Jenkins to pull source code from GitHub.
- Configured the main branch for the build.

### 2. Jenkins Configuration
- Created a Freestyle Jenkins job named `JOB-2`.
- Configured GitHub repository URL.
- Added Maven build commands in the Execute Shell section.

### 3. Maven Build

Used the following command to clean and deploy the application:

```bash
mvn clean deploy
```

Maven performs the following operations:
- Cleans previous build files.
- Compiles the Java application.
- Runs configured tests.
- Packages the application into a WAR file.
- Deploys the artifact to the configured repository.

### 4. Nexus Integration

Configured Nexus credentials in Maven `settings.xml`.

Example configuration:

```xml
<settings>
    <servers>
        <server>
            <id>NexusRepo</id>
            <username>admin</username>
            <password>K@rthik@2004</password>
        </server>
    </servers>
</settings>
```

**Note:** The repository ID in `settings.xml` must match the repository ID configured in `pom.xml`.

### 5. Tomcat Deployment

- Configured a remote Tomcat 9 server in Jenkins.
- Added Tomcat deployment credentials.
- Configured the deployment context path as `MKP-PRODUCTION`.
- Jenkins deploys the generated WAR file to Tomcat.

## Troubleshooting

### Maven XML Parsing Error

**Error:**
```text
Non-parseable settings.xml
end tag name </server> must match start tag name <settings>
```

**Solution:**
- Corrected the XML opening and closing tags.
- Ensured the `<server>` element was inside `<servers>`.
- Ensured the `<servers>` element was inside `<settings>`.

### Maven Command Error

Incorrect:
```bash
mvn clean Deploy
```

Correct:
```bash
mvn clean deploy
```

Maven goals should use lowercase letters.

## Expected Output

- Jenkins successfully checks out the GitHub repository.
- Maven builds the application.
- WAR artifact is generated.
- Artifact is published to Nexus when configured.
- Jenkins deploys the WAR file to Tomcat.
- Application becomes accessible through the Tomcat server.

## Learning Outcomes

- Hands-on experience with Jenkins CI/CD pipelines.
- Integration of GitHub with Jenkins.
- Building Java applications using Maven.
- Configuring Nexus Repository Manager.
- Deploying WAR files to Apache Tomcat.
- Troubleshooting Maven configuration and deployment errors.

## Followed This Doucement

https://devopscube.com/how-to-install-latest-sonatype-nexus-3-on-linux/# 

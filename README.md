It is command for run Docker Image Of Jenkins:- 
    docker run -p 8081:8080 -p 50000:50000 -v jenkins_home:/var/jenkins_home jenkins/jenkins:lts

Excellent! Let’s fully break down **Task 8: Run a Simple Java Maven Build Job in Jenkins** — including:

* ✅ What the task is asking you to do
* 🔧 Why it's important in DevOps and the industry
* 🧑‍💻 What your role is as a DevOps engineer
* ⚙️ Step-by-step how to complete it
* 🧠 What you learn from this

---

## 🔍 What is this task about?

You are setting up a **Jenkins Freestyle job** to compile and build a simple Java application using **Maven**.

This is your **first step into CI/CD (Continuous Integration/Continuous Delivery)**.

---

## ✅ Why is this task needed?

### 🧱 In real DevOps & Software teams:

* Developers **write code** (Java, Python, etc.)
* DevOps Engineers **automate building, testing, and deploying** this code
* **Jenkins** is a CI/CD tool that automates all these steps
* **Maven** is a build tool for Java projects

So this task helps you understand **how to build Java code automatically using Jenkins** — the same way it's done in real companies.

---

## 🧑‍💻 Your Role as a DevOps Engineer

| Responsibility          | What You’ll Do in This Task                        |
| ----------------------- | -------------------------------------------------- |
| CI/CD Automation        | Set up Jenkins to auto-build Java code             |
| Build Tools Integration | Configure Maven in Jenkins                         |
| Job Configuration       | Create a Jenkins job to compile & package the app  |
| Log Monitoring          | Check Jenkins Console Output for errors or success |

This is **exactly what DevOps engineers do** in a pipeline.

---

## 💡 Where is this used in industry?

In almost every tech company:

* Developers **push Java code** to GitHub/GitLab
* Jenkins **automatically builds and tests** the code using Maven
* Then Jenkins **deploys it** (to Docker, AWS, Kubernetes, etc.)

Your task is covering **the "build" phase** of this lifecycle.

---

## 🚀 Step-by-Step Guide: How to Do It

---

### 1️⃣ Create the Java App

**Project Structure:**

```
hello-java-maven/
├── pom.xml
└── src/
    └── main/
        └── java/
            └── HelloWorld.java
```

#### 🔹 `HelloWorld.java`

```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, Jenkins + Maven!");
    }
}
```

#### 🔹 `pom.xml`

```xml
<project>
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.example</groupId>
  <artifactId>hello</artifactId>
  <version>1.0</version>
  <build>
    <plugins>
      <plugin>
        <groupId>org.apache.maven.plugins</groupId>
        <artifactId>maven-compiler-plugin</artifactId>
        <version>3.8.1</version>
        <configuration>
          <source>1.8</source>
          <target>1.8</target>
        </configuration>
      </plugin>
    </plugins>
  </build>
</project>
```

---

### 2️⃣ Start Jenkins with Docker

```bash
docker run -p 8081:8080 -p 50000:50000 -v jenkins_home:/var/jenkins_home jenkins/jenkins:lts
```

* Access Jenkins: `http://localhost:8080`
* Unlock Jenkins: Use the password from the terminal output (`/var/jenkins_home/secrets/initialAdminPassword`)

---

### 3️⃣ Set up Jenkins Tools

1. Go to: **Manage Jenkins → Global Tool Configuration**
2. Under **Maven**:

   * Click **Add Maven**
   * Name: `Maven 3.8.6`
   * Install automatically (or use a local path)
3. Do the same for **JDK** if needed

---

### 4️⃣ Create the Jenkins Freestyle Project

1. Click: **New Item**

2. Name it: `hello-java-maven`

3. Select: **Freestyle project**

4. Under **Source Code Management**:

   * (Optional) Use Git if your project is on GitHub
   * OR leave it empty if you're building from a local path

5. Under **Build Section**:

   * Click **Add build step → Invoke top-level Maven targets**
   * Goals: `clean package`

---

### 5️⃣ Build and Verify

* Click **Build Now**
* Go to **Console Output**
* You should see: `BUILD SUCCESS`

🎉 Congrats! Your first Java CI job is done.

---

## 🔎 What You'll Learn from This Task

| Concept            | Skill Gained                                 |
| ------------------ | -------------------------------------------- |
| Jenkins Job Basics | Creating and running a job manually          |
| CI/CD Fundamentals | Automating a build process                   |
| Maven Integration  | Using Maven to compile and package Java code |
| Console Output     | Reading and troubleshooting build logs       |

---

## 💼 Bonus: Real-World Extension

* Connect the Jenkins job to GitHub
* Automatically trigger the build when code is pushed
* Add **JUnit tests** to run during build
* Deploy to a **Tomcat Server** or **Docker container**

---

Let me know when you're ready for the **next CI/CD step**, like:

* Triggering builds via GitHub Webhooks
* Running tests automatically
* Deploying to staging or production servers

Want help writing the full `pom.xml` or setting up GitHub integration? Just say the word!

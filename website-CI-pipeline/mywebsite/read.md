# 📘 Level 1 DevOps Documentation

## Continuous Integration (CI) using Azure DevOps Pipelines

---

## 👋 Introduction

This document explains **Level 1 DevOps** in a **beginner-friendly and practical way**.
The focus of Level 1 is **Continuous Integration (CI)**.

In this level, we automate the process of:

* Taking website code from Git repository
* Running an Azure Pipeline automatically
* Creating an **artifact** whenever code changes

This is the **first real DevOps step** used in companies.

---

## 🎯 Objective of Level 1

> Whenever code is pushed to the repository:
>
> * Pipeline runs automatically
> * Website files are collected
> * An artifact is generated

No server deployment is involved in Level 1.

---

## 🧰 Tools Used

| Tool            | Purpose                |
| --------------- | ---------------------- |
| Azure Repos     | Store website code     |
| Azure Pipelines | Automate CI process    |
| YAML            | Pipeline configuration |
| Git             | Version control        |

---

## 🗂️ Project Structure

```
repo-root
│
├── website
│   └── index.html
│
└── azure-pipelines.yml
```

---

## 📄 Website File

**Path:** `website/index.html`

```html
<!DOCTYPE html>
<html>
  <body>
    <h1>Hello DevOps 😊</h1>
    <p>This is my first CI pipeline</p>
  </body>
</html>
```

This is a simple static website used for CI testing.

---

## ⚙️ Azure Pipeline YAML File

**Path:** `azure-pipelines.yml`

```yaml
trigger:
- main

pool:
  vmImage: ubuntu-latest

steps:
- checkout: self

- task: CopyFiles@2
  inputs:
    SourceFolder: 'website'
    Contents: '**'
    TargetFolder: '$(Build.ArtifactStagingDirectory)/website'

- task: PublishBuildArtifacts@1
  inputs:
    pathToPublish: '$(Build.ArtifactStagingDirectory)/website'
    artifactName: website-artifact
```

---

## 🧠 YAML Explanation (Simple)

### 1️⃣ Trigger

```yaml
trigger:
- main
```

* Pipeline runs automatically when code is pushed to `main` branch

---

### 2️⃣ Agent Pool

```yaml
pool:
  vmImage: ubuntu-latest
```

* Azure provides a Linux machine to run the pipeline

---

### 3️⃣ Checkout Code

```yaml
- checkout: self
```

* Downloads repository code to the pipeline machine

---

### 4️⃣ Copy Website Files

```yaml
- task: CopyFiles@2
```

* Copies website files from repo to staging directory

---

### 5️⃣ Publish Artifact

```yaml
- task: PublishBuildArtifacts@1
```

* Creates a downloadable artifact (ZIP file)
* Artifact name: `website-artifact`

---

## 📦 What is an Artifact?

An **artifact** is the final output of the pipeline.

In this project:

* Artifact contains website files
* Artifact proves that CI ran successfully

Artifacts are stored **inside pipeline runs**, not in the repository.

---

## 🔁 CI Validation Test

### Step 1: Modify Website

Change text in `index.html`:

```html
<h1>Hello DevOps 🚀 Updated</h1>
```

### Step 2: Commit & Push

```bash
git commit -am "Updated website text"
git push
```

### Step 3: Observe

* Pipeline runs automatically
* New artifact is created
* Updated content appears inside artifact

This confirms **Continuous Integration works**.

---

## ✅ Outcome of Level 1

After completing Level 1, you understand:

| Concept         | Status |
| --------------- | ------ |
| CI              | ✅      |
| Azure Pipelines | ✅      |
| YAML basics     | ✅      |
| Artifacts       | ✅      |
| Auto trigger    | ✅      |

---

## 🚀 Next Step

Level 2 introduces **Continuous Deployment (CD)** where:

* Artifact is deployed
* Apache server is used
* Website updates automatically on a Linux VM

---

## 🏁 Conclusion

Level 1 DevOps builds the foundation for real-world CI pipelines.
This approach is widely used for freshers and beginners in DevOps roles.

---

✅ **Level 1 Completed Successfully**

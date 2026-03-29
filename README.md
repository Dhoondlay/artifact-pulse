# 🩺 Artifact-Pulse | DevArtifact

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Java Version](https://img.shields.io/badge/Java-17%2B-blue)](https://www.oracle.com/java/technologies/javase/jdk17-archive-downloads.html)
[![Build Status](https://github.com/Dhoondlay/devartifact/actions/workflows/maven.yml/badge.svg)](https://github.com/Dhoondlay/devartifact/actions)

**Artifact-Pulse** is a high-performance, non-invasive Java Instrumentation Agent designed for real-time observability in distributed systems and AI-integrated backends.

By leveraging the native `java.lang.instrument` API, Pulse performs **runtime bytecode manipulation** to inject telemetry directly into your application. It allows developers to monitor "Hot Paths" and method latency with nanosecond precision—**without modifying a single line of source code.**

---

## 🧐 Why Artifact-Pulse?

In the era of **Agentic Workflows** and microservices, understanding where time is spent is critical. Traditional profilers are often too heavy for production, and manual logging is tedious. 

**Pulse** solves this by:
* **Zero-Code Instrumentation:** Attach the agent at startup; no recompilation needed.
* **Transparent Monitoring:** Profile third-party libraries or internal code identically.
* **Minimal Overhead:** Uses optimized ByteBuddy instructions to ensure your application stays fast.

---

## 🛠️ Technical Architecture

Artifact-Pulse operates as a **ClassFileTransformer**. When the JVM loads a class, Pulse intercepts the byte array, analyzes the methods, and "wraps" them with timing logic.



### The "Pulse" Hook:
1.  **Entry:** Records `System.nanoTime()`.
2.  **Execution:** The original method logic runs.
3.  **Exit:** Calculates the delta and "pulses" the data to the console or log.

---

## 🚀 Getting Started

### 1. Prerequisites
* Java 17 or higher.
* Maven 3.8+ (for building from source).

### 2. Build the Artifact
```powershell
mvn clean package
This generates artifact-pulse-1.0.0.jar in the target/ directory.

3. Attach the Agent
To start monitoring your application, add the -javaagent argument to your startup command:

Bash
java -javaagent:path/to/artifact-pulse.jar -jar your-application.jar
📊 Example Output
When Pulse is active, your logs will provide real-time latency telemetry:

Plaintext
[Pulse] 🩺 Agent Active: Monitoring com.dhoondlay.*
[Pulse] 🩺 Method: com.dhoondlay.api.AIService.generateResponse() -> 142.5ms
[Pulse] 🩺 Method: com.dhoondlay.db.UserRepo.findValidUser() -> 8.2ms
[Pulse] 🔥 ALERT: Hot Path Detected in 'generateResponse' (>100ms)
🏗️ Project Structure
src/main/java/.../agent/PulseAgent.java: The entry point for the JVM.

src/main/java/.../agent/PulseTransformer.java: The bytecode manipulation logic.

pom.xml: Configuration for the JAR Manifest and ByteBuddy dependencies.

🤝 Contributing
We welcome contributions to the Dhoondlay ecosystem! Whether it's optimizing the bytecode transformer or adding new "Pulse" exporters (like Prometheus or Jaeger), feel free to open a PR.

Fork the Project.

Create your Feature Branch (git checkout -b feature/AmazingFeature).

Commit your Changes (git commit -m 'Add AmazingFeature').

Push to the Branch (git push origin feature/AmazingFeature).

Open a Pull Request.

📜 License
Distributed under the MIT License. See LICENSE for more information.

Built with ❤️ by Dhoondlay for the Open Source Community.

---

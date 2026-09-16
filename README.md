# LLM Comparison Using Spring AI

A Spring Boot and React application for sending the same prompt to OpenAI,
Anthropic, and a local Ollama model and comparing their responses.

## Features

- Spring AI integrations for OpenAI, Anthropic, and Ollama
- REST endpoints for each model provider
- React/Vite frontend for comparing model responses
- Ollama support for running models locally

## Technology

- Java 21
- Spring Boot 3.4.3
- Spring AI 1.0.0-M6
- Maven
- React 19 and Vite 6

## Project Structure

```text
.
├── src/main/java/com/nakul/SpringAIDemo/  # Spring Boot backend
├── src/main/resources/                    # Application configuration
├── src/main/llm-comparison-ui/            # React frontend
├── src/test/                              # Backend tests
├── pom.xml
└── mvnw
```

## Prerequisites

- JDK 21 or newer
- Node.js and npm
- Internet access for OpenAI and Anthropic
- Ollama installed locally if you want to use the Ollama integration

## Setup

Clone the repository:

```bash
git clone https://github.com/nakuldagade/LLM-Comparison-Using-SpringAI.git
cd LLM-Comparison-Using-SpringAI
```

### Backend configuration

Add the provider keys to `src/main/resources/application.properties`.
Do not commit real API keys.

```properties
spring.application.name=SpringAIDemo
spring.ai.openai.api-key=your_openai_api_key
spring.ai.anthropic.api-key=your_anthropic_api_key
spring.ai.ollama.chat.options.model=deepseek-r1:14b
```

For Ollama, install and start Ollama, then download the configured model:

```bash
ollama serve
ollama pull deepseek-r1:14b
```

Run the backend from the repository root:

```bash
./mvnw spring-boot:run
```

On Windows, use `mvnw.cmd spring-boot:run`.

The backend runs on `http://localhost:8080`.

### Frontend setup

In a separate terminal:

```bash
cd src/main/llm-comparison-ui
npm install
npm run dev
```

Vite prints the local frontend URL, normally `http://localhost:5173`.

## API Endpoints

Each endpoint accepts the prompt as a URL path variable:

```text
GET /api/openai/{message}
GET /api/anthropic/{message}
GET /api/ollama/{message}
```

Example:

```bash
curl http://localhost:8080/api/ollama/Explain%20Spring%20AI
```

## Useful Commands

```bash
# Run backend tests
./mvnw test

# Build the backend
./mvnw clean package

# Build the frontend
cd src/main/llm-comparison-ui
npm run build

# Check frontend lint
npm run lint
```

## License

This project is available for personal and educational use.

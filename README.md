# 🎌 AnimePahe API

> A lightweight, free-to-use AnimePahe scraper API designed to make anime data and streaming information easy to access from your own applications.

[![GitHub](https://img.shields.io/badge/GitHub-Repository-black?style=for-the-badge&logo=github)](https://github.com/kaustuklol/AnimePahe-API)
[![Vercel](https://img.shields.io/badge/Deploy-Vercel-black?style=for-the-badge&logo=vercel)](https://vercel.com/)
[![API](https://img.shields.io/badge/API-REST-blue?style=for-the-badge)](#-api-endpoints)
[![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)](#-license)

---

## ✨ Overview

**AnimePahe API** is an unofficial scraper/API built to provide developers with an easy way to retrieve anime information without having to build their own scraper from scratch.

The project is designed with simplicity in mind:

**Anime Website → Scraper → REST API → Your Application**

You can use it as the backend for:

- 🎬 Anime streaming websites
- 🔎 Anime search applications
- 📱 Anime mobile applications
- 🤖 Discord/Telegram bots
- 🧪 Personal projects
- 🎓 Learning projects
- 🌐 Custom anime frontends

The API can be deployed independently and consumed by any frontend or application capable of making HTTP requests.

---

## 🚀 Features

- 🔍 **Anime Search** — Search anime by title
- 📺 **Episode Data** — Retrieve episode information
- 🎞️ **Streaming Sources** — Retrieve available streaming sources
- 🖼️ **Anime Metadata** — Titles, posters and related information
- ⚡ **Lightweight** — Designed to keep the API simple and easy to deploy
- 🌍 **Free to Use** — Use your own deployed instance for your projects
- ☁️ **Vercel Ready** — Designed for easy serverless deployment
- 🔌 **REST API** — Easy to integrate with any frontend or application
- 🛠️ **Open Source** — Fork it, modify it and build on top of it

---

## 🧩 How It Works

The project acts as a bridge between an anime source website and your application.

```text
                    ┌─────────────────┐
                    │   Anime Source  │
                    │    Website      │
                    └────────┬────────┘
                             │
                             ▼
                    ┌─────────────────┐
                    │     Scraper     │
                    │  Data Extraction │
                    └────────┬────────┘
                             │
                             ▼
                    ┌─────────────────┐
                    │   REST API      │
                    │    Backend      │
                    └────────┬────────┘
                             │
                    JSON Response
                             │
                             ▼
              ┌───────────────────────────┐
              │       Your Application    │
              │                           │
              │  Website / App / Bot etc. │
              └───────────────────────────┘
```

This means your frontend doesn't need to directly understand how the source website works.

---

# 📡 API Endpoints

> The exact endpoints available depend on the current implementation in the repository.

### 🔎 Search Anime

```http
GET /search?q=naruto
```

Search for anime using a title or keyword.

Example:

```bash
curl "https://YOUR-API.vercel.app/search?q=naruto"
```

---

### 📺 Get Episodes

```http
GET /episodes?session=ANIME_SESSION
```

Retrieve episodes associated with an anime session.

Example:

```bash
curl "https://YOUR-API.vercel.app/episodes?session=YOUR_SESSION"
```

---

### 🎬 Get Streaming Sources

```http
GET /sources?anime_session=ANIME_SESSION&episode_session=EPISODE_SESSION
```

Retrieve available sources for a specific episode.

Example:

```bash
curl "https://YOUR-API.vercel.app/sources?anime_session=YOUR_SESSION&episode_session=YOUR_EPISODE_SESSION"
```

---

## 📦 Example Response

A search request can return structured JSON that can be directly consumed by a frontend:

```json
[
  {
    "id": 123,
    "title": "Example Anime",
    "url": "https://example.com/anime/example",
    "year": 2025,
    "poster": "https://example.com/poster.jpg",
    "type": "TV",
    "session": "example-session"
  }
]
```

Episode information can similarly be represented as structured objects:

```json
[
  {
    "id": 12345,
    "number": 1,
    "title": "Episode 1",
    "snapshot": "https://example.com/snapshot.jpg",
    "session": "episode-session"
  }
]
```

---

# 💻 Using the API

The API can be consumed from practically any programming language.

### JavaScript

```javascript
const response = await fetch(
  "https://YOUR-API.vercel.app/search?q=naruto"
);

const data = await response.json();

console.log(data);
```

### Python

```python
import requests

url = "https://YOUR-API.vercel.app/search"

response = requests.get(
    url,
    params={"q": "naruto"}
)

data = response.json()

print(data)
```

### cURL

```bash
curl "https://YOUR-API.vercel.app/search?q=naruto"
```

---

# ☁️ Deploy on Vercel

One of the main goals of this project is to make deployment as simple as possible.

### 1. Fork the repository

Fork this repository to your own GitHub account.

```text
https://github.com/kaustuklol/AnimePahe-API
```

### 2. Open Vercel

Go to:

```text
https://vercel.com/
```

Create a new project and import your forked repository.

### 3. Deploy

Configure the project according to the repository's included Vercel configuration and click:

**Deploy**

After deployment, Vercel will provide you with an API URL similar to:

```text
https://your-project.vercel.app
```

You can then use that URL from your frontend.

### Example

```javascript
const API_URL = "https://your-project.vercel.app";

fetch(`${API_URL}/search?q=one%20piece`)
  .then(res => res.json())
  .then(data => console.log(data));
```

---

# 🛠️ Run Locally

Clone the repository:

```bash
git clone https://github.com/kaustuklol/AnimePahe-API.git
```

Enter the project:

```bash
cd AnimePahe-API
```

Install the required dependencies according to the project's package/dependency files.

Then start the application using the project's configured development/start command.

Your local API will be available at the local address printed by the server.

---

# 🏗️ Use It With Your Own Anime Website

This project becomes especially useful when combined with a custom frontend.

For example:

```text
                    AnimePahe API
                          │
             ┌────────────┼────────────┐
             │            │            │
             ▼            ▼            ▼
          Search       Episodes     Sources
             │            │            │
             └────────────┼────────────┘
                          ▼
                    Your Frontend
                          │
                          ▼
                    Video Player
```

---

# 📁 Project Structure

The exact structure may evolve as the project develops, but the repository is organized around the scraper/API workflow:

```text
AnimePahe-API/
│
├── api/              # API/serverless entry points
├── scraper/          # Scraping/data extraction logic
├── requirements.txt  # Python dependencies
├── vercel.json       # Vercel configuration
├── main.py           # Application entry point
└── README.md         # Documentation
```

> If your current repository uses different filenames/folders, update this section to match the actual tree.

---

# ⚙️ Architecture

The project follows a simple request flow:

```text
Client
  │
  │ HTTP Request
  ▼
API Endpoint
  │
  ▼
Scraper
  │
  │ Request
  ▼
Anime Source
  │
  │ HTML / API Data
  ▼
Parser
  │
  ▼
Structured JSON
  │
  ▼
Client
```

This keeps the frontend independent from the scraping logic.

---

# 🌟 Why This Project?

Anime websites can change their page structure, request methods and data formats frequently.

Instead of writing scraping logic inside every individual project, this API provides a reusable layer:

```text
Without API:

Frontend
   ↓
Scraping Logic
   ↓
Anime Website


With AnimePahe API:

Frontend
   ↓
AnimePahe API
   ↓
Scraping Logic
   ↓
Anime Website
```

This makes it easier to reuse the same backend across multiple projects.

---

# 🔥 Possible Projects You Can Build

You can use this API as the backend for:

### 🎬 Anime Streaming Website

Build your own frontend with:

- Anime search
- Home page
- Anime details
- Episode lists
- Video player
- Watch history
- Bookmarks

### 📱 Mobile Application

Use the API as a backend for an Android/iOS anime application.

### 🤖 Discord Bot

Create commands such as:

```text
/anime naruto
/episodes naruto
/watch naruto 1
```

# ⚠️ Important Notes

This project is an **unofficial scraper** and is not affiliated with, endorsed by, or sponsored by AnimePahe.

The project does not claim ownership of any anime content or media returned by the scraper.

The availability and structure of scraped data may change if the source website changes its implementation.

If the source website becomes unavailable or changes its protection/structure, parts of the API may stop working until the scraper is updated.

**Use this project responsibly and respect the terms, policies and applicable laws of the services you access.**

---

# 🛡️ Responsible Usage

If you deploy your own public instance:

- Avoid excessive requests
- Consider implementing rate limiting
- Do not intentionally overload the source website
- Cache responses where appropriate
- Monitor your deployment's resource usage
- Respect applicable terms of service and copyright laws

For production applications, consider putting your API behind appropriate caching and request controls.

---

# 🤝 Contributing

Contributions are welcome!

If you have an improvement, bug fix or new feature:

1. Fork the repository
2. Create a new branch

```bash
git checkout -b feature/my-feature
```

3. Make your changes
4. Commit your changes

```bash
git commit -m "Add my feature"
```

5. Push the branch

```bash
git push origin feature/my-feature
```

6. Open a Pull Request

---

# ⭐ Support the Project

If you find this project useful:

- ⭐ Star the repository
- 🍴 Fork it
- 🐛 Report bugs
- 💡 Suggest improvements
- 🔧 Submit pull requests

Every star and contribution helps the project grow.

---

# 👨‍💻 Developer

Built by **Kaustuk Jaiswal**

GitHub:

**https://github.com/kaustuklol**

Repository:

**https://github.com/kaustuklol/AnimePahe-API**

---

# 📄 License

This project is open source and available under the **MIT License**.

See the `LICENSE` file for more information.

---

<p align="center">
  Made with ❤️ and lots of ☕ by <b>Kaustuk Jaiswal</b>
</p>

<p align="center">
  If this project helped you, consider giving it a ⭐
</p>

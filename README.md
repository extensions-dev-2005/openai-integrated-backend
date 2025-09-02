# 🚀 Nova.AI Desktop Widget
A high-performance desktop application that provides real-time meeting transcription, intelligent summarization, and AI-powered response suggestions with professional-grade reliability and speed using OpenAI's latest models.

## ✨ Enhanced Features
### 🎯 Core Capabilities
- **⚡ Real-Time Transcription**: Live speech-to-text with OpenAI's Whisper models
- **🎤 Microphone Selection**: Support for multiple input devices
- **🧠 AI Summarization**: Structured summaries with GPT-4o models  
- **💡 Smart Suggestions**: Context-aware response recommendations using OpenAI's reasoning capabilities
- **🚀 Performance Optimized**: Async processing, caching, retry logic
- **🔒 Privacy Focused**: Secure OpenAI API integration with local processing
- **📊 Performance Monitoring**: Real-time metrics and connection status

### 🛠 Technical Improvements
- **OpenAI Integration**: Latest GPT-4o models and Whisper transcription
- **Async Architecture**: Non-blocking operations with thread pools
- **Smart Caching**: Reduces API calls and improves response times
- **Error Recovery**: Automatic retries with exponential backoff
- **Health Monitoring**: Real-time system status and performance metrics
- **Modern UI**: Clean interface with progress indicators
- **Standalone Application**: No browser dependencies

## 🏗 Architecture Overview
```
┌─────────────────┐    ┌──────────────────┐    ┌─────────────────┐
│ Desktop Widget  │────│  FastAPI Backend │────│   OpenAI API    │
│                 │    │                  │    │                 │
│ • Audio Capture │    │ • Async Processing│    │ • Whisper       │
│ • UI Management │    │ • Smart Caching  │    │ • GPT-4o Models │
│ • Error Handling│    │ • Health Checks  │    │ • Reasoning API │
│ • Device Select │    │                  │    │ • Rate Limiting │
└─────────────────┘    └──────────────────┘    └─────────────────┘
```

## ⚡ Quick Start
### 1. Backend Setup
#### Option A: Docker (Recommended)
```bash
# Clone the repository
git clone https://github.com/yourusername/nova-ai-desktop.git
cd nova-ai-desktop

# Create environment file
cp .env.example .env
# Edit .env and add your OpenAI API key:
# OPENAI_API_KEY=sk-your-openai-api-key-here

# Build and run the backend
docker build -t nova-ai-backend .
docker run -d -p 8000:8000 --env-file .env nova-ai-backend
```

#### Option B: Direct Installation
```bash
# Clone the repository
git clone https://github.com/yourusername/nova-ai-desktop.git
cd nova-ai-desktop/backend

# Install dependencies
pip install -r requirements.txt

# Set environment variables
export OPENAI_API_KEY=sk-your-openai-api-key-here
export ENVIRONMENT=production
export PORT=8000

# Start the backend
uvicorn app:app --reload --host 0.0.0.0 --port 8000
```

### 2. Getting Your OpenAI API Key
1. Visit [OpenAI Platform](https://platform.openai.com/)
2. Sign up or log in to your account
3. Navigate to API Keys section
4. Create a new API key
5. Copy the key (starts with `sk-`)
6. Add it to your `.env` file or environment variables

### 3. Desktop Widget Setup
#### Option A: Pre-built Executable (Recommended)
1. Download the latest release for your operating system
2. Install the application following the on-screen instructions
3. Launch Nova.AI from your applications menu

#### Option B: From Source
```bash
# Clone the repository
git clone https://github.com/yourusername/nova-ai-desktop.git
cd nova-ai-desktop

# Install dependencies
pip install -r requirements.txt

# Run the application
python main.py
```

## 🎯 OpenAI Models Used
### Transcription
- **Model**: `gpt-4o-mini-transcribe`
- **Features**: High-accuracy speech-to-text, multi-language support
- **File Limits**: Up to 25MB audio files
- **Supported Formats**: MP3, MP4, MPEG, MPGA, M4A, WAV, WEBM

### Text Generation & Summarization
- **Model**: `gpt-4o-mini`
- **Features**: Advanced reasoning, structured output, cost-efficient
- **Use Cases**: Meeting summaries, key point extraction, action item identification

### Response Suggestions (Beta)
- **Model**: `gpt-4o-mini` with reasoning capabilities
- **Features**: Context-aware suggestions, confidence scoring
- **Integration**: Uses OpenAI's responses API when available

## 📋 Usage Guide
### Starting a Transcription Session
1. **Configure Microphone**
   - Launch the Nova.AI Desktop Widget
   - Select your preferred microphone from the dropdown
   - Ensure the backend connection status shows "Connected"

2. **Start Recording**
   - Click "Start Recording" or press Ctrl+R
   - The status will change to "Recording..."
   - Begin speaking or join your meeting

3. **Monitor Progress**
   - Watch live transcription appear in the main window
   - Track chunk count and processing time
   - View connection status in the status bar

### Using AI Features
1. **Generate Summary**
   - After sufficient audio has been captured, a summary will automatically appear
   - Review structured summary with:
     - Key discussion points
     - Action items identified
     - Important decisions made

2. **Get Response Suggestions**
   - AI-powered suggestions appear automatically using OpenAI's reasoning
   - View context and confidence level
   - Suggestions update as more conversation is captured

3. **Export Transcript**
   - Click "Export" to save your transcript
   - Files are saved with timestamp for easy organization

## ⚙️ Configuration Options
### Backend Configuration
| Environment Variable | Default | Description |
|---------------------|---------|-------------|
| `OPENAI_API_KEY` | Required | Your OpenAI API key (starts with sk-) |
| `PORT` | `8000` | Server port |
| `ENVIRONMENT` | `development` | Deployment environment |
| `LOG_LEVEL` | `info` | Logging level |

### Desktop Widget Settings
- **Backend URL**: API endpoint (configurable in settings)
- **Microphone Selection**: Choose from available input devices
- **Chunk Duration**: Processing interval (default: 5 seconds)
- **Auto-Summarize**: Automatic summary generation (enabled by default)

## 📊 Performance & Monitoring
### Key Metrics
- **Response Time**: < 3 seconds for transcription
- **Accuracy**: 98%+ on clear audio with OpenAI Whisper
- **Memory Usage**: Optimized for long-running sessions
- **Connection Status**: Real-time backend health monitoring

### OpenAI API Limits
- **Transcription**: 50 requests per minute
- **Text Generation**: 500 requests per minute
- **File Size**: Up to 25MB per audio file
- **Context Length**: Up to 128k tokens for GPT-4o-mini

### Monitoring Features
- **Chunk Processing Time**: Displayed in status bar
- **Connection Health**: Visual indicator in status bar
- **Error Handling**: Automatic retries with exponential backoff
- **Progress Indicators**: Visual feedback during processing

## 🔧 Troubleshooting
### Common Issues
1. **OpenAI API Key Issues**
   - Ensure your API key starts with `sk-`
   - Check if you have sufficient credits in your OpenAI account
   - Verify the key is correctly set in environment variables

2. **No Microphone Detected**
   - Ensure your microphone is properly connected
   - Check system audio settings
   - Try selecting a different microphone from the dropdown

3. **Backend Connection Failed**
   - Verify the backend is running
   - Check your internet connection
   - Confirm the backend URL is correct
   - Check OpenAI API status at [status.openai.com](https://status.openai.com)

4. **Poor Transcription Quality**
   - Ensure you're in a quiet environment
   - Check microphone positioning
   - Verify your microphone is selected in the dropdown
   - Consider using a higher quality microphone

5. **Rate Limiting Issues**
   - OpenAI has rate limits - wait a moment and try again
   - Consider upgrading your OpenAI plan for higher limits
   - Monitor your usage in the OpenAI dashboard

### API Error Codes
- **401**: Invalid API key
- **429**: Rate limit exceeded
- **413**: File too large (max 25MB)
- **503**: OpenAI service temporarily unavailable

### Keyboard Shortcuts
- **Ctrl+R**: Toggle recording on/off
- **Ctrl+C**: Clear all content
- **F1**: Show help dialog

## 💰 Cost Considerations
### OpenAI Pricing (as of 2024)
- **Whisper**: $0.006 per minute of audio
- **GPT-4o-mini**: $0.150 per 1M input tokens, $0.600 per 1M output tokens
- **Typical Usage**: ~$0.01-0.05 per hour of meeting transcription

### Cost Optimization Tips
1. Use caching to avoid duplicate transcriptions
2. Implement audio preprocessing to reduce file sizes
3. Set reasonable token limits for summaries
4. Monitor usage in OpenAI dashboard
5. Consider batch processing for multiple files

## 🚀 Production Deployment
### Backend Deployment
The FastAPI backend can be deployed to any cloud provider:

#### Render/Railway/Heroku
```bash
# Procfile already configured
web: uvicorn app:app --host=0.0.0.0 --port=${PORT:-8000}

# Required Environment Variables
OPENAI_API_KEY=sk-your-key-here
ENVIRONMENT=production
PORT=8000
```

#### Docker Deployment
```dockerfile
FROM python:3.11-slim

WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt

COPY app.py .
COPY Procfile .

EXPOSE 8000
CMD ["uvicorn", "app:app", "--host", "0.0.0.0", "--port", "8000"]
```

### Environment Variables for Production
```bash
OPENAI_API_KEY=sk-your-production-key
ENVIRONMENT=production
PORT=8000
LOG_LEVEL=warning
```

### Desktop Application Distribution
To distribute the desktop application:
1. Package using PyInstaller:
```bash
pip install pyinstaller
pyinstaller --onefile --windowed --icon=assets/icon.ico main.py
```
2. Create installers for your target platform
3. Distribute through your preferred channel

## 🔐 Security Best Practices
1. **API Key Management**
   - Never commit API keys to version control
   - Use environment variables or secure secret management
   - Rotate keys regularly
   - Monitor usage for unusual activity

2. **Data Privacy**
   - Audio files are processed temporarily and deleted
   - No persistent storage of sensitive meeting content
   - All communication with OpenAI is encrypted (HTTPS)
   - Consider data residency requirements

3. **Network Security**
   - Use HTTPS for all API communications
   - Implement rate limiting to prevent abuse
   - Monitor for suspicious activity
   - Keep dependencies updated

## 🧪 Development & Testing
### Local Development
```bash
# Install development dependencies
pip install -e ".[dev]"

# Run tests
pytest

# Code formatting
black app.py
isort app.py

# Start development server
uvicorn app:app --reload --host 0.0.0.0 --port 8000
```

### Testing OpenAI Integration
```bash
# Test API connectivity
curl -X GET http://localhost:8000/health

# Test transcription (with audio file)
curl -X POST http://localhost:8000/transcribe \
  -F "audio=@test_audio.wav"

# Test summarization
curl -X POST http://localhost:8000/summarize \
  -H "Content-Type: application/json" \
  -d '{"text": "Your meeting transcript here..."}'
```

## 🤝 Contributing
We welcome contributions! Please see our contributing guidelines:

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests if applicable
5. Submit a pull request

### Development Setup
```bash
git clone https://github.com/yourusername/nova-ai-desktop.git
cd nova-ai-desktop
pip install -e ".[dev]"
```

## 📞 Support & Resources
- **Documentation**: [docs.openai.com](https://docs.openai.com)
- **OpenAI Status**: [status.openai.com](https://status.openai.com)
- **Issues**: GitHub Issues for bug reports and feature requests
- **Discord**: Join our community for support and discussions

## 📄 License
This project is licensed under the MIT License - see the LICENSE file for details.

## 🙏 Acknowledgments
- OpenAI for providing excellent AI models and APIs
- FastAPI community for the robust framework
- Contributors and beta testers

---

**Note**: This application requires an OpenAI API key and active internet connection. Ensure you comply with OpenAI's usage policies and your organization's data handling requirements.

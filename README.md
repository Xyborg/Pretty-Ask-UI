# Pretty Ask UI - Interactive LLM DNS Query Interface

A beautiful command-line interface for querying Large Language Models (LLMs) through DNS TXT records. This script provides a GUI-like experience in the terminal with server selection, chat mode, and input validation.

## Features

- 🌐 **Multiple Server Support** - Easy configuration for multiple LLM DNS servers
- 💬 **Interactive Chat Mode** - Continuous conversation with the AI
- 📏 **Input Validation** - Automatic DNS query length validation (63/253 character limits)
- 🎨 **Beautiful UI** - Box-drawing characters and color-coded interface
- ⚡ **Quick Queries** - Single-shot questions via command line arguments
- 🔄 **Server Switching** - Change servers on-the-fly during chat
- 📱 **Terminal Responsive** - Adapts to your terminal width

## Prerequisites

- Bash shell (compatible with macOS and Linux)
- `dig` command (usually pre-installed)
- Terminal with color support

## Installation

1. Download the script:
```bash
curl -O https://raw.githubusercontent.com/Xyborg/Pretty-Ask-UI/main/pretty-ask-ui
chmod +x pretty-ask-ui
```

2. Or clone the repository and make it executable:
```bash
git clone https://github.com/Xyborg/Pretty-Ask-UI.git
cd Pretty-Ask-UI
chmod +x pretty-ask-ui
```

## Usage

### Interactive Chat Mode
Start the script without arguments for continuous conversation:
```bash
./pretty-ask-ui
```

### Single Query Mode
Ask a quick question:
```bash
./pretty-ask-ui "what is machine learning"
./pretty-ask-ui "write hello world in python"
```

## Server Configuration

The script comes pre-configured with several servers. Edit the `SERVERS` array at the top of the script to add your own:

```bash
SERVERS=(
    "ch.at|ch.at|53"
    "LLM Pieter|llm.pieter.com|9000"
    "Local|localhost|5354"
    # Add your servers here:
    # "My Server|my-llm.example.com|8080"
)
```

Format: `"Display Name|hostname|port"`

### Default Servers

1. **ch.at** - Public DNS server (ch.at:53)
2. **LLM Pieter** - Pieter's LLM server (llm.pieter.com:9000)
3. **Local** - Local development server (localhost:5354)

## Commands (Interactive Mode)

- `help` or `h` - Show available commands and examples
- `switch` or `s` - Change to a different server
- `clear` or `cls` - Clear the chat history
- `quit`, `exit`, `q`, or `:q` - Exit the application

## DNS Query Limits

The script enforces DNS specification limits:

- **63 characters** - Maximum for single DNS label (strict validation)
- **253 characters** - Maximum total query length (warning shown)

When you exceed 63 characters, the script will prompt you to try a shorter question.

## Examples

### Starting a Chat Session
```bash
$ ./pretty-ask-ui
┌──────────────────────────────────────────────────────────────────────┐
│                    🌐 Choose Your LLM Server                         │
└──────────────────────────────────────────────────────────────────────┘

Available servers:
[1] ch.at (ch.at)
[2] LLM Pieter (llm.pieter.com:9000)
[3] Local (localhost:5354)

Choose server [1-3]: 2
✓ Selected: LLM Pieter (llm.pieter.com:9000)

┌──────────────────────────────────────────────────────────────────────┐
│              🧠 LLM DNS Query Interface via LLM Pieter               │
└──────────────────────────────────────────────────────────────────────┘

💬 Chat Mode - Type your questions naturally
💡 Commands: help, switch, clear, q (quit)
Current server: LLM Pieter (llm.pieter.com:9000)
📝 Keep queries under 63 characters for best DNS compatibility

👤 You: what is golang
🤖 AI:
  Go (also known as Golang) is an open-source programming language 
  developed by Google. It was created by Robert Griesemer, Rob Pike, 
  and Ken Thompson and first released in 2009...
```

### Quick Single Query
```bash
$ ./pretty-ask-ui "explain DNS"
┌──────────────────────────────────────────────────────────────────────┐
│              🧠 LLM DNS Query Interface via LLM Pieter               │
└──────────────────────────────────────────────────────────────────────┘

👤 You: explain DNS
🤖 AI:
  DNS (Domain Name System) is like the phonebook of the internet. 
  It translates human-readable domain names (like google.com) into 
  IP addresses (like 172.217.14.206) that computers use to identify 
  each other on the network...

─────────────────────────────────────────────────────────────────
LLM DNS Chat | Press Ctrl+C to exit
```

## Troubleshooting

### Connection Issues

If you see connection errors:

1. **Local Server**: Make sure your local LLM DNS server is running.

2. **Remote Servers**: The server might be down or unreachable. Try switching to another server using the `switch` command.

3. **Network Issues**: Check your internet connection and firewall settings.

### Query Too Long

If your question is too long:
- Try breaking it into smaller, more specific questions
- Remove unnecessary words while keeping the core meaning
- Use abbreviations where appropriate

## Technical Details

- **Protocol**: DNS TXT record queries
- **Character Encoding**: UTF-8 with automatic decoding
- **Terminal Compatibility**: Works with most modern terminals
- **Response Formatting**: Automatic word wrapping and clean text formatting

## Contributing

1. Fork the repository
2. Create a feature branch: `git checkout -b feature-name`
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## License

This project is open source. Please check the repository for license details.
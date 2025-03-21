# Exa RAG Demo with OpenAI and Live Web Crawling

This repository demonstrates how to build a powerful Retrieval Augmented Generation (RAG) system using Exa's search API with OpenAI and live web crawling capabilities. The demo showcases both a custom RAG implementation and Exa's integrated answer endpoint.

## Features

- **Dual RAG Implementation**:
  - Custom pipeline with full control over each step
  - Simplified implementation using Exa's `/answer` endpoint

- **Live Web Crawling**:
  - Access real-time web content for up-to-date information
  - Fetch fresh data from pages not yet in Exa's index

- **Rich Content Processing**:
  - Retrieve and process full page contents
  - Use highlighted text snippets for focused context
  - Generate well-cited responses with source attribution

## Requirements

- Python 3.8+
- Exa API key (sign up at [exa.ai](https://exa.ai))
- OpenAI API key

## Installation

1. Clone this repository:
   ```bash
   git clone https://github.com/yourusername/exa-rag-demo.git
   cd exa-rag-demo
   ```

2. Create a virtual environment and activate it:
   ```bash
   python -m venv venv
   
   # On Windows
   venv\Scripts\activate
   
   # On macOS/Linux
   source venv/bin/activate
   ```

3. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

4. Set up your environment variables:
   ```bash
   cp .env.example .env
   ```
   Then edit the `.env` file to add your API keys.

## Usage

Run the demo with a query:

```bash
# Using custom RAG implementation (default)
python exa_rag_demo.py "What are the latest advancements in AI?"

# Using Exa's integrated answer endpoint
python exa_rag_demo.py "What are the latest advancements in AI?" --method exa

# Enable live web crawling for real-time data
python exa_rag_demo.py "Recent developments in AI safety" --live-crawl

# Specify number of search results to use
python exa_rag_demo.py "Global AI policy updates" --results 10

# Specify a different OpenAI model
python exa_rag_demo.py "Quantum computing breakthroughs" --model gpt-3.5-turbo
```

## How It Works

### Custom RAG Implementation

1. **Retrieval**: Uses Exa's search API to find relevant content based on the query
2. **Content Augmentation**: Optionally fetches full page contents for deeper analysis
3. **Generation**: Constructs a prompt with retrieved information and uses OpenAI to generate a response

### Exa's Integrated Endpoint

Uses Exa's `/answer` endpoint which:
1. Automatically performs a search for the query
2. Uses an integrated LLM (GPT-4o-mini) to generate a response
3. Returns both the answer and the sources used

## Advanced Configuration

You can customize various aspects of the demo:

- **Search Parameters**: Adjust autoprompt, highlighting, and number of results
- **LiveCrawl Settings**: Enable/disable real-time web crawling
- **Model Selection**: Choose different OpenAI models for response generation
- **Streaming**: Enable streaming responses for real-time output (commented code available)

## Project Structure

```
exa-rag-demo/
├── exa_rag_demo.py   # Main implementation
├── requirements.txt  # Python dependencies
├── .env.example      # Example environment variables
├── .env              # Your actual environment variables (git-ignored)
└── README.md         # This documentation
```

## Further Development

Here are some ways you could extend this demo:

1. **Web Interface**: Create a simple UI using Flask or Streamlit
2. **Advanced Filtering**: Add domain filtering, date ranges, or content types
3. **Chunking Strategy**: Implement different text chunking and embedding approaches
4. **Hallucination Detection**: Add verification mechanisms using Exa's capabilities
5. **Streaming Responses**: Enable token-by-token streaming of generated content

## Resources

- [Exa Documentation](https://docs.exa.ai)
- [OpenAI API Documentation](https://platform.openai.com/docs/api-reference)
- [RAG with Exa and OpenAI Guide](https://docs.exa.ai/reference/rag-quickstart.md)

## License

This project is licensed under the MIT License - see the LICENSE file for details.
# AI Model Evaluation Suite for JSON Generation & Hallucination Detection

This project uses [PromptFoo](https://promptfoo.dev/) to evaluate multiple AI models on their ability to generate valid JSON and detect hallucinations across various scenarios.

## 🚀 Features

- **Multi-Model Testing**: Evaluate 5 different AI models simultaneously
- **JSON Generation Tests**: Test basic to complex JSON structure generation
- **Hallucination Detection**: Advanced tests for factual consistency, uncertainty handling, and attribution verification
- **Automated Assertions**: JavaScript-based validation for test outcomes
- **Comprehensive Reporting**: Detailed results across all models and test cases

## 🤖 Models Tested

| Provider | Model | Description |
|----------|-------|-------------|
| Google | Gemini 2.5 Flash | Google's latest multimodal model |
| Anthropic | Claude 3.5 Sonnet | Advanced reasoning and coding capabilities |
| OpenAI | GPT-4.1 Mini | Efficient and cost-effective GPT model |
| Meta | Llama 3.1 70B | Large language model with strong reasoning |
| Qwen | Qwen 2.5 72B | Multilingual model with strong coding abilities |

## 📋 Test Cases

### JSON Generation Tests
1. **Simple JSON**: Basic user object generation
2. **Nested JSON**: Complex objects with nested structures
3. **JSON Arrays**: Array generation with multiple items
4. **Edge Cases**: Ambiguous requests and boundary conditions

### Hallucination Detection Tests
5. **Factual Consistency - Real Person**: Verify correct information for known figures
6. **Factual Consistency - Fictional Person**: Detect when models correct misleading information
7. **Uncertainty Check**: Handle requests for unknown future information
8. **Self-Contradiction**: Identify logical inconsistencies
9. **Fake References**: Detect fabricated citations and sources

## 🛠️ Setup

### Prerequisites

- Node.js (v16 or higher)
- npm or yarn
- Git

### Installation

1. **Clone the repository**:
   ```bash
   git clone <your-repo-url>
   cd PromptFoo/JSON
   ```

2. **Install PromptFoo**:
   ```bash
   npm install -g promptfoo
   ```

3. **Set up API keys**:

   Create a `.env` file in the project root:

   ```env
   GEMINI_API_KEY=your_google_gemini_api_key
   OPENROUTER_API_KEY_1=sk-or-v1-your_anthropic_key
   OPENROUTER_API_KEY_2=sk-or-v1-your_openai_key
   OPENROUTER_API_KEY_3=sk-or-v1-your_meta_key
   OPENROUTER_API_KEY_4=sk-or-v1-your_qwen_key
   ```

   **Getting API Keys:**
   - **Google Gemini**: Get from [Google AI Studio](https://makersuite.google.com/app/apikey)
   - **OpenRouter**: Get from [OpenRouter](https://openrouter.ai/) (supports multiple providers)

## 🚀 Usage

### Run All Tests

```bash
promptfoo eval
```

This will run all 9 test cases across all 5 models (45 total evaluations).

### Run Specific Tests

```bash
# Run only JSON generation tests
promptfoo eval --filter-pattern "JSON"

# Run only hallucination tests
promptfoo eval --filter-pattern "Hallucination"

# Run a specific test case
promptfoo eval --filter-pattern "Test Case 1"
```

### View Results

```bash
# Open web-based results viewer
promptfoo view
```

## 📊 Understanding Results

### Pass/Fail Criteria

- **JSON Tests**: Must generate valid JSON and meet specific content requirements
- **Hallucination Tests**: Must either provide correct information or explicitly indicate uncertainty/fabrication

### Common Failure Patterns

- **Invalid JSON**: Malformed JSON syntax
- **Missing Content**: Required fields not present
- **Hallucinations**: Incorrect factual information presented as truth
- **Poor Uncertainty Handling**: Making up information instead of admitting unknowns

## 🔧 Configuration

### Adding New Models

Edit `promptfooconfig.yaml`:

```yaml
providers:
  - id: openrouter:new-model-name
    config:
      apiKey: ${OPENROUTER_API_KEY_5}
```

### Adding New Tests

Add to the `tests` section in `promptfooconfig.yaml`:

```yaml
- description: 'Your Test Description'
  vars:
    task: 'Your prompt here'
  assert:
  - type: 'is-json'
  - type: 'javascript'
    value: 'your_custom_validation_logic'
```

## 📈 Advanced Usage

### Custom Assertions

Use JavaScript for complex validation:

```javascript
// Check for specific content
output.includes("expected_text")

// Parse and validate JSON structure
JSON.parse(output).field === "value"

// Complex logic
(output.includes("A") && output.includes("B")) || output.includes("alternative")
```

### Performance Comparison

```bash
# Compare model performance
promptfoo eval --filter-pattern "all" --output results.json
```

### Continuous Integration

Add to your CI pipeline:

```yaml
- name: Run AI Model Tests
  run: |
    npm install -g promptfoo
    promptfoo eval --ci
```

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Add your test cases or model configurations
4. Run tests to ensure they pass
5. Submit a pull request

## 📚 Resources

- [PromptFoo Documentation](https://promptfoo.dev/docs/)
- [OpenRouter Models](https://openrouter.ai/models)
- [Google Gemini API](https://ai.google.dev/docs)
- [AI Hallucination Research](https://arxiv.org/abs/2305.12574)

## ⚠️ Security Notes

- Never commit API keys to version control
- Use environment variables for all sensitive data
- Rotate API keys regularly
- Monitor usage to avoid unexpected costs

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 🙏 Acknowledgments

- [PromptFoo](https://promptfoo.dev/) for the excellent testing framework
- [OpenRouter](https://openrouter.ai/) for unified API access
- All the AI model providers for their amazing technology

---

**Happy Testing!** 🎯
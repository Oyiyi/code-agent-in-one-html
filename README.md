
## Run Locally

**Prerequisites:**  Node.js

1. Install dependencies:
   `npm install`

2. Set the `GEMINI_API_KEY` in [.env](.env) to your Gemini API key

3. Run the app:
   `npm run dev`

## Technical Overview

### Interactive Mode
- **Loop**: 15 tool calls max per user request
- **Error handling**: Graceful fallbacks for API failures, tool errors logged and flow continues
- **Model**: Gemini 2.5 Flash with stepwise reasoning instructions

### Memory Mechanism  
- **Hybrid memory**: Short-term (recent messages) + long-term (extracted facts, vector docs, static blocks)
- **Context**: Working set (active file/folder/selection) always prepended
- **Persistence**: localStorage snapshot with import/export

### Tools Available
- **Read ops**: `list_files`, `read_file`, `search_files`, `get_file_info`
- **Write ops**: `write_local_file`, `create_local_directory`, `delete_local_file` 
- **File ops**: `move_file`, `read_text_file`
- **No MCP**: Uses Gemini's native function calling

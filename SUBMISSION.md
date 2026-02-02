# TRP1 - AI-Content Generation Challenge Submission

**Candidate:** Addisu Taye

## Environment Setup
Installed `uv` CLI on Windows: `irm https://astral.sh/uv/install.ps1 | iex` → `uv --version`. Navigated to project folder and copied `.env.example` to `.env`. Synced project: `uv sync`. Verified installation: `uv run ai-content --help`, `uv run ai-content list-providers`, `uv run ai-content list-presets`. Outcome: CLI functional; environment ready.

## Codebase Exploration
`src/ai_content/providers/` contains providers: `google/lyria.py` (instrumental music), `aimlapi/minimax.py` (vocals), `veo.py` (video). `pipelines/` orchestrates content generation. CLI commands: `uv run ai-content music`, `uv run ai-content video`, `uv run ai-content list-providers`, `uv run ai-content list-presets`. Insights: prompts required, MiniMax requires lyrics file, Lyria is instrumental only, Veo video API may be deprecated.

## Content Generation
**Music (Lyria/Gemini):** `uv run ai-content music --prompt "Upbeat motivational instrumental with smooth jazz saxophone and piano" --style jazz --provider lyria --duration 30`. Output: ✅ `exports\lyria_20260202_122945.wav` generated (30s jazz instrumental).  
**Video (Veo/Google GenAI):** `uv run ai-content video --prompt "Peaceful nature scene with flowing river and trees, cinematic style" --style nature --provider veo --duration 5`. Result: ❌ Failed: `module 'google.genai.types' has no attribute 'GenerateVideoConfig'`. Attempted `pip install --upgrade google-genai` → error persists. Video not generated due to library/API mismatch; documented as troubleshooting.

## Challenges & Solutions
- `uv` not recognized → added `$env:USERPROFILE\.local\bin` → works  
- MiniMax music failed initially → added `--lyrics lyrics.txt` → 403 error due to unverified account  
- AIMLAPI 403 forbidden → switched to Gemini (Lyria) → success  
- Veo video error → documented; unable to generate

## Insights & Learnings
- CLI options (`--prompt`, `--lyrics`) are mandatory  
- Lyria is simpler; MiniMax requires verification and lyrics  
- Video generation sensitive to library versions  
- Documenting attempts/troubleshooting is crucial  
- Prompts influence output style and quality

## Artifacts
- Music: `exports\lyria_20260202_122945.wav`  
- Video: not generated  
- Commands run: included above  
- Lyrics file: `lyrics.txt` used for MiniMax testing

## YouTube / GitHub Links
- YouTube: Video generation attempted but failed. 
- GitHub repo: https://github.com/Addisu-Taye/TRP-1-AI-Content-Generation-Challeng

**Notes:** Music generation succeeded. Video generation attempted but failed. All commands, prompts, and troubleshooting are documented. Submission demonstrates exploration, persistence, and understanding of the codebase.

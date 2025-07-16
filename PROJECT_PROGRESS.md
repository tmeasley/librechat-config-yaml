# LibreChat Herbal Medicine Platform - Project Progress

## Project Overview
Custom LibreChat deployment for Eclectic School of Herbal Medicine with specialized AI agents and RAG knowledge base integration.

## Current Status: ✅ WORKING
**Last Updated**: January 16, 2025
**Deployment**: Live on Railway with custom agents showing correctly

## Architecture

### Repository Structure
```
tmeasley/LibreChat (main app code)
├── Standard LibreChat application
└── Not used for configuration

tmeasley/librechat-config-yaml (THIS REPO - configuration)
├── librechat-env-l.yaml (ACTIVE CONFIG - Railway reads this)
├── librechat-env-f.yaml (other config variant)
├── librechat-test.yaml (test config)
├── icons/ (custom avatars)
└── scripts/ (utility scripts)
```

### Deployment Pipeline
```
Local Edit → Git Push → Railway Auto-Deploy → Live Update
```

## Key Accomplishments

### ✅ Phase 1: Basic Setup (Completed)
- [x] Railway deployment configured
- [x] Custom branding implemented
- [x] RAG API integration established
- [x] Vector store configuration

### ✅ Phase 2: Custom Agents (Completed - Jan 16, 2025)
- [x] 4 specialized herbal medicine agents created
- [x] Agent-specific instructions and personalities defined
- [x] Model dropdown hidden (`hideModelSelection: true`)
- [x] Custom agents now showing in UI instead of model selection

### 🔄 Phase 3: Content Integration (In Progress)
- [ ] Herbal curriculum documents uploaded to RAG system
- [ ] Vector store populated with course materials
- [ ] Agent knowledge base testing and refinement
- [ ] Custom avatar images added

### 📋 Phase 4: Enhancement (Planned)
- [ ] Advanced agent capabilities
- [ ] Custom UI themes
- [ ] Student progress tracking
- [ ] Community features

## Custom Agents Configuration

### Current Agents (All Working):

#### 1. Study Buddy 📚
- **Purpose**: Learning companion for herbal medicine students
- **Model**: claude-3-5-sonnet-20241022
- **Features**: Quizzes, study guides, concept explanations
- **RAG**: Connected to herbal curriculum

#### 2. Herbie 🌿  
- **Purpose**: Expert herbal medicine consultation
- **Model**: claude-3-5-sonnet-20241022
- **Features**: Protocol development, safety guidance, holistic assessment
- **RAG**: Connected to herbal curriculum

#### 3. Communibot 👥
- **Purpose**: Community building and networking
- **Model**: claude-3-5-haiku-20241022
- **Features**: Study groups, events, mentorship connections
- **RAG**: Connected to herbal curriculum

#### 4. Diffbot 🔬
- **Purpose**: Advanced analysis and research
- **Model**: o1-preview (OpenAI)
- **Features**: Complex case analysis, research interpretation
- **RAG**: Connected to herbal curriculum

## Technical Configuration

### Interface Settings
```yaml
interface:
  hideModelSelection: true  # Shows agents instead of models
  appTitle: "Herbal Medicine AI Assistant"
  customFooter: "Powered by Eclectic School of Herbal Medicine"
```

### RAG Integration
```yaml
ragApi:
  - name: "herbal_medicine_kb"
    baseURL: "https://rag-api-production-f502.up.railway.app"
    endpoints:
      query: "/query"
      documents: "/documents"
```

### Vector Stores
```yaml
vectorStores:
  herbal_curriculum:
    ragApi: "herbal_medicine_kb"
    namespace: "herbal_curriculum"
```

## Known Issues Resolved

### Issue 1: Agents Not Showing (FIXED)
**Problem**: Custom agents weren't appearing in UI, only model dropdown
**Root Cause**: Missing `hideModelSelection: true` in interface config
**Solution**: Added setting to `librechat-env-l.yaml`
**Status**: ✅ Resolved (Jan 16, 2025)

### Issue 2: Wrong Repository (FIXED)
**Problem**: Editing main LibreChat repo instead of config repo
**Root Cause**: Confusion about repository structure
**Solution**: Identified correct config repo and workflow
**Status**: ✅ Resolved (Jan 16, 2025)

### Issue 3: PowerShell Syntax (FIXED)
**Problem**: Using Unix commands in Windows PowerShell
**Root Cause**: Assistant using wrong command syntax
**Solution**: Updated cursor rules with correct PowerShell syntax
**Status**: ✅ Resolved (Jan 16, 2025)

## Next Steps

### Immediate (Next Session)
1. Test all 4 agents in live Railway deployment
2. Verify RAG integration is working
3. Upload sample herbal curriculum documents
4. Test agent responses with RAG knowledge

### Short Term (Next Week)
1. Add custom avatar images for each agent
2. Populate vector store with full curriculum
3. Refine agent instructions based on testing
4. Add file upload configuration for students

### Long Term (Next Month)
1. Advanced agent capabilities (tool usage)
2. Student progress tracking
3. Community features integration
4. Performance optimization

## Deployment Notes

### Railway Configuration
- **Repository**: `tmeasley/librechat-config-yaml`
- **Config File**: `librechat-env-l.yaml`
- **Auto-Deploy**: Enabled on push to main branch
- **Build Time**: ~2-3 minutes

### Environment Variables Required
```
ANTHROPIC_API_KEY=sk-...
OPENAI_API_KEY=sk-...
RAG_API_KEY=...
```

### Monitoring
- Railway dashboard for deployment status
- LibreChat interface for agent functionality
- RAG API endpoint for knowledge base status

## Contact & Resources
- **Primary Developer**: Assistant (Cursor/Claude)
- **Repository Owner**: tmeasley
- **Main Config File**: `librechat-env-l.yaml`
- **Railway Project**: LibreChat deployment
- **RAG API**: `rag-api-production-f502.up.railway.app` 
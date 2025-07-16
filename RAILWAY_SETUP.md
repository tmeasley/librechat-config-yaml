# Railway LibreChat Setup Guide

## Problem Solved: Custom Agents Not Showing

**Root Cause**: LibreChat didn't know where to find the custom configuration file.

**Solution**: Set the `CONFIG_PATH` environment variable in Railway.

## ✅ **Step-by-Step Fix:**

### 1. Add Environment Variable in Railway

1. Go to [railway.app](https://railway.app)
2. Open your LibreChat project
3. Navigate to **Variables** or **Environment** tab
4. Click **New Variable**
5. Add:
   - **Name**: `CONFIG_PATH`
   - **Value**: `https://raw.githubusercontent.com/tmeasley/librechat-config-yaml/main/librechat-env-l.yaml`
6. Click **Save**

### 2. Redeploy

Railway should automatically redeploy when you add the environment variable.

### 3. Verify

After deployment:
- Visit your LibreChat URL
- Refresh the page
- You should now see your 4 custom agents instead of model dropdown:
  - 📚 Study Buddy
  - 🌿 Herbie
  - 👥 Communibot
  - 🔬 Diffbot

## 🔄 **Future Updates Workflow:**

Now that `CONFIG_PATH` is set, any changes to `librechat-env-l.yaml` will automatically update your Railway deployment:

1. Edit `librechat-env-l.yaml` in this repository
2. Commit and push changes
3. Railway reads the updated file via the raw GitHub URL
4. Changes appear in your LibreChat instance

## 🎯 **What This CONFIG_PATH Does:**

- Tells LibreChat to read configuration from the specified URL
- Railway downloads the config file on startup
- Enables all custom settings including:
  - ✅ `hideModelSelection: true` (shows agents instead of models)
  - ✅ Custom app title: "Herbal Medicine AI Assistant"
  - ✅ Custom footer branding
  - ✅ 4 specialized agents with RAG integration
  - ✅ Vector store configuration
  - ✅ File upload settings

## 📋 **Environment Variables Needed in Railway:**

| Variable | Value |
|----------|-------|
| `CONFIG_PATH` | `https://raw.githubusercontent.com/tmeasley/librechat-config-yaml/main/librechat-env-l.yaml` |
| `ANTHROPIC_API_KEY` | Your Anthropic API key |
| `OPENAI_API_KEY` | Your OpenAI API key |
| `RAG_API_KEY` | Your RAG API key (if required) |

## 🚨 **Important Notes:**

- The URL must be the **raw** GitHub URL (starts with `raw.githubusercontent.com`)
- Changes to config file take effect on next Railway deployment
- Environment variables in Railway override any settings in the config file
- Make sure your repository is **public** or Railway can't access the config file

## 🎉 **Success Indicators:**

When working correctly, you should see:
- No model dropdown in the UI
- 4 custom agent cards with names and descriptions
- Custom app title in browser tab
- Custom footer text
- RAG integration working with agents 
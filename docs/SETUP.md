# Setup Guide for Auto-Deploy Agent

## Prerequisites

Before setting up the Auto-Deploy Agent, ensure you have:
- Node.js (v14 or higher)
- npm or yarn
- Git
- SSH access to deployment servers
- GitHub personal access token

## Installation Steps

### 1. Clone the Repository
```bash
git clone https://github.com/DigitalVertise/auto-deploy-agent.git
cd auto-deploy-agent
```

### 2. Install Dependencies
```bash
npm install
```

### 3. Configure Environment Variables
Copy the example environment file and update with your configuration:
```bash
cp .env.example .env
```

Edit `.env` with your specific values:
```
GITHUB_TOKEN=your_github_token
DEPLOY_TOKEN=your_deployment_token
STAGING_SERVER=your_staging_server
PRODUCTION_SERVER=your_production_server
```

### 4. Set Up SSH Keys
Ensure SSH keys are properly configured:
```bash
ssh-keygen -t rsa -b 4096 -f ~/.ssh/id_rsa
chmod 600 ~/.ssh/id_rsa
```

### 5. Test Installation
```bash
npm start
npm run deploy:dev
npm test
```

## Docker Setup (Optional)

Build Docker image:
```bash
docker build -t auto-deploy-agent .
```

Run in Docker:
```bash
docker run --env-file .env auto-deploy-agent
```

## Troubleshooting Setup Issues

### Issue: Module not found
**Solution:** Run `npm install` again and check for errors

### Issue: EACCES permission errors
**Solution:** Update npm permissions:
```bash
mkdir ~/.npm-global
npm config set prefix '~/.npm-global'
```

### Issue: SSH connection failed
**Solution:** Verify SSH key permissions and server access:
```bash
ssh -i ~/.ssh/id_rsa user@server
```

## Next Steps

1. Read [CONFIG.md](./CONFIG.md) for detailed configuration options
2. Review [API.md](./API.md) for API endpoints
3. Check the main [README.md](../README.md) for usage examples

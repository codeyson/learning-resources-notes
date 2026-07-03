# Deployment

Step 1: Choice of Hosting 
Step 2: API Design
Step 3: How to run
    Options:
    1. Containers
    2. Serverless functions
    3. CLoud managed services

## CI/CD

### Continuous Integration (CI):
1. Source: Retrieve source code
2. Build: Create a container image containing the code
3. Test: Perform integration tests
4. Register: Store the container in a registry

### Continuous Deployment (CD):
1. Retrieve: Retrieve container from registry
2. Test: Perform deployment tests
3. Deploy: Deploy container to environments:
    - Staging
    - Production

## Scaling
- LLM might need specialized GPU

- Scaling Strategies:
    1. Horizontal: Add more machines
    2. Vertical: Boosting one machine

    // Horizontal for traffic, vertical for reliability and speed.

# Monitoring and Observability
- **Monitoring** continuously watches a system.
- **Observability** reveals internal states of external observer

1. Data sources for observability
    - Logs
    - Metrics
    - Traces

# Types of Monitoring
1. Input Monitoring
2. Functional Monitoring
3. Output Monitoring

// Alert handle after monitoring

# Cost Management
1. Focus on model cost
2. Hosting vs Usage
    - Self-hosted models, cost arise from hosting.
    - Externally hosted models, cost arise from usage.

## Strategy to lower cost

Strategy 1: Choose the right model
    - Use most cost-effective model that can do the task.
    - Use multiple smaller task-specific models

Strategy 2: Optimize prompts
    - Use automatic prompt compression
    - Content reduction
    - Optimize RAG to return fewer results

Strategy 3: Optimize the number of calls
    - Use batching
    - Response caching
    - Optimize (and limit) agent calls
    - Set quota and rate limits
    - Consider tasks which don't require LLMs
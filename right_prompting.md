# Right Prompting Techniques for QA & Testing

### 1. Generate 5 Basic Login Test Cases
**Technique:** Zero-Shot Prompting
**Reasoning:** LLMs are trained on massive datasets where login operations are common. They can generate standard positive and negative scenarios without additional context.

### 2. Analyze a Complex Bug with Multiple Symptoms
**Technique:** Chain of Thought (CoT) Prompting
**Reasoning:** Complex debugging requires a step-by-step breakdown. We instruct the LLM to analyze each symptom sequentially, identifying potential links and filtering through possibilities until the root cause or primary symptom is finalized.

### 3. Generate Test Cases in Custom Company Template
**Technique:** Few-Shot Prompting
**Reasoning:** Since the company template is proprietary or specific, providing a few examples (shots) helps the LLM understand the required structure, tone, and specific fields (like "Priority" or "Requirement ID") used in the organization.

### 4. Quick Validation of Input Field
**Technique:** Zero-Shot Prompting
**Reasoning:** Input fields (text, email, password) follow standard validation rules (regex, length, special characters) that the LLM already "knows" from its training data.

### 5. Root Cause Analysis of Intermittent Failure
**Technique:** Chain of Thought (CoT) Prompting
**Reasoning:** Intermittent failures are difficult to diagnose. By guiding the LLM step-by-step—asking it to consider environment variables, race conditions, and logs—we arrive at a logical conclusion for the failure.

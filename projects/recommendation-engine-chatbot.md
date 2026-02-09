Case Study 1: Real Time Manufacturing Breakdown Recommendation System

Context
In a high throughput manufacturing environment, equipment breakdowns directly impact cycle time and productivity. Resolution knowledge existed across historical logs, PDFs, and spreadsheets, but technicians relied on manual searches and tribal knowledge, leading to delays and inconsistent fixes.

Problem
How can technicians get fast, reliable breakdown resolution guidance without digging through scattered documentation, while ensuring the system continuously improves over time?

Approach
I designed and built a GPT powered internal chatbot that provided real time breakdown resolution recommendations using historical error resolution mappings.

Parsed structured Excel logs and unstructured PDF documents into a unified knowledge base

Implemented similarity based retrieval to match live errors with historical resolutions

Designed a feedback loop where technician validated fixes were captured and ranked

Ensured responses were context aware and constrained to verified enterprise knowledge

Due to confidentiality, internal systems and datasets cannot be shared.

Tools and Technologies
Python, Azure OpenAI, NLP, Excel and PDF parsing, similarity search, FastAPI

Impact

Reduced downtime by accelerating root cause identification

Improved consistency in breakdown resolution across shifts

Created a self improving system through technician feedback

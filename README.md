# Resume-Optimiser
Here's a sample GitHub README description for your AI Resume Optimizer project. Feel free to modify any sections to better fit your style or add additional details.

```markdown
# AI Resume Optimizer

## Overview
The AI Resume Optimizer is a Python-based application that leverages OpenAI's GPT-3.5 to enhance resumes based on specific job descriptions. This project aims to help job seekers tailor their resumes, ensuring they highlight the most relevant skills and experiences to stand out to potential employers.

## Features
- **PDF to Markdown Conversion**: Convert existing PDF resumes into a more editable markdown format.
- **Job Description Adaptation**: Automatically revise and optimize resumes to align with job descriptions provided by users.
- **Markdown to PDF Conversion**: Convert the optimized markdown resumes back into PDF format for easy sharing.

## Technologies Used
- Python
- OpenAI API
- Markdown
- PDF Libraries (e.g., `pdfkit`, `markdown2`)

## Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/ai-resume-optimizer.git
   cd ai-resume-optimizer
   ```

2. Install the required packages:
   ```bash
   pip install openai pdfkit markdown2
   ```

3. Set up your OpenAI API key:
   - You can either hardcode your API key into the script or set it as an environment variable:
   ```bash
   export OPENAI_API_KEY='your_openai_api_key'  # For macOS/Linux
   set OPENAI_API_KEY='your_openai_api_key'  # For Windows
   ```

## Usage
To optimize a resume based on a job description, use the following code:

```python
from openai import OpenAI
import os

# Initialize OpenAI client with API key from environment variable
client = OpenAI(api_key=os.getenv('OPENAI_API_KEY'))

def optimize_resume(markdown_resume, job_description):
    # Define the single prompt message
    prompt = f"""
    Here is a resume in markdown format:

    {markdown_resume}

    Here is the job description:

    {job_description}

    Please revise the resume so it highlights the skills, achievements, and experiences that match the job description.
    """

    # Send the prompt as a single message to the ChatCompletion endpoint
    response = client.completions.create(
        model="gpt-3.5-turbo-instruct",
        prompt=prompt,
        max_tokens=1500,
        temperature=0
    )

    optimized_resume = response['choices'][0]['text'].strip()
    return optimized_resume

# Example usage
job_description = "Your job description here."
markdown_resume = "Your markdown resume here."
optimized_resume = optimize_resume(markdown_resume, job_description)
print(optimized_resume)
```

## Contributing
Contributions are welcome! Please feel free to submit a pull request or open an issue for any suggestions or improvements.

## Acknowledgements
- [OpenAI](https://openai.com/) for providing the API used in this project.
- [Markdown](https://daringfireball.net/projects/markdown/) for enabling easy formatting.

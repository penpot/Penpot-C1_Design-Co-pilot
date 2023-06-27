# Approach #3 | New layout generation
    
The system will take user input about the desired layout and generate a new page based on the existing elements. The idea is to utilize a top-down approach, first generating a layout, after - populating it with elements. 

| Technology readiness | Risks | Complexity |
| ----- | ----- | ---------- |
| <div style="width: 200"> 🟡 Some elements are available, but further development and research needed | <div style="width: 150pt"> 🟡 Moderate risk | <div style="width: 130pt"> 🔴 Complex |

## Technology

Pre-process SVG layouts →  Clean by place holding elements 
→ Input to LLM Model 
→ Model output high-level layout based on the prompt 
→ Post-process by replacing placeholders with SVG 
→ Output the final layout.

## Relevant works

[Research]

- Layout generation [[Paper](references/research_papers/LayoutFormer++.pdf)]

- Layout generation with Transformers [[Paper](references/research_papers/GUILGET.pdf)]

[Business solutions]

- Galileo AI · Copilot for interface design [[Website](https://www.usegalileo.ai/)]

- WireGen - AI GPT wireframe generation [[Figma Plug-in](https://www.figma.com/community/plugin/1221144015267698736/WireGen---AI-GPT-wireframe-generation)]

- Builder.io - Generate designs with AI & export to code [[Figma Plug-in](https://www.figma.com/community/plugin/747985167520967365/Builder.io---Generate-designs-with-AI-&-export-to-code/Builder.io---Generate-designs-with-AI-&-export-to-code)]

## Pros and Cons

🟢 Pros

- The ability to generate new layouts based on user inputs and existing elements allows for highly adaptive and custom designs
- The model generates a high-level layout based on the prompt, which would save computation cost and time for outputting full-length SVG with content.

🔴 Cons

- No respective open-source Github repo is available for checking the performance of the research paper
- Generation quality has the risk of not meeting the designer's requirements since there is limited research on SVG generation
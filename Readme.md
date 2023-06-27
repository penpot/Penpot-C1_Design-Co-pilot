# Idea #1 | Design Co-pilot

## 🔎 Idea overview

Designers create the design and design system, and the co-pilot can do routine tasks such as transferring this design to other pages where you don’t need to be creative just transfer this design. So you can act like a junior designer creating content based on created design. It leaves control to the designer but can augment and scale the activities.

## 💡 Feature analysis
### Approach #1 | Editing SVG elements
    
The system will allow users to edit the SVG UI elements by describing their desired changes in a text format, which will then be interpreted by a chatGPT-like system and applied to the SVG element.

| Technology readiness | Risks | Complexity |
| ----- | ----- | ---------- |
| 🟢 Ready for implementation | <div style="width: 100pt"> 🟡 Moderate risk | <div style="width: 150pt"> 🟠 Moderately complex |


**Technologies**

Following LLM for SVG editing [[Paper](references/Research%20papers/LLM_for_SVG_Editing.pdf)], the input can be an optimized SVG with text instructions to edit it. The language Model can be tuned on the created target dataset using raster-to-vector tools. 

🖼️ **Visualization**

| Demo #1 | Demo #2 | Demo #3 |
| --- | --- | --- |
| <div style="width: 170pt"> ![SVGEditDemo1.png](reports/figures/SVGEditDemo1.png) | <div style="width: 170pt"> ![SVGEditDemo2.png](reports/figures/SVGEditDemo2.png) | <div style="width: 170pt"> ![SVGEditDemo3.png](reports/figures/SVGEditDemo3.png) |

**Requirements**

- ML model: LLM
- SVG optimizer: SVGO [[Github](https://github.com/svg/svgo)]
- Raster-to-vector tool:
    - Vectorisation [[Tutorial](https://blog.thea.codes/raster-vectorization-with-python/)][[Sample code](https://gist.github.com/theacodes/2e13e4e05700279734ca4b34df370adb)]
    - Vtracer [[Github](https://github.com/visioncortex/vtracer)]
- Input: SVG component + text prompt
- Output: edited SVG component
<details>
<summary>Dataset: Open-source SVG components with text description for finetuning LLM</summary>

- Iconify: >150,000 open source SVG icons [[Website](https://iconify.design/)] [[Description](https://iconify.design/docs/icons/icon-data.html)] [[Figma Plug-in](https://www.figma.com/community/plugin/735098390272716381/Iconify)] [[Figma Plug-in Github](https://github.com/iconify/iconify-figma)]
    
- FIGR-8: containing **17,375 classes** of **1,548,256 images** representing pictograms, ideograms, icons, emoticons or object or conception depictions (*with both png and svg format*) [[Github](https://github.com/marcdemers/FIGR-8)]
    
    ![dataset_explanation.png](reports/figures/dataset_explanation.png)
    
- SVG Repo: with 500,000+ open-licensed SVG vector and icons [[Website](https://www.svgrepo.com/)]
            
</details>

**Relevant works**

[Research]

- LLM for SVG editing [[Paper](references/Research%20papers/LLM_for_SVG_Editing.pdf)]

- LLM for image editing [[Github](https://github.com/IDEA-Research/GroundingDINO/blob/main/demo/image_editing_with_groundingdino_gligen.ipynb)]: GroundingDINO [[Github](https://github.com/IDEA-Research/GroundingDINO)] + GLIGEN [[Github](https://github.com/gligen/GLIGEN)]

- Text prompt for image editing: InstructPix2Pix [[Github](https://github.com/timothybrooks/instruct-pix2pix)]；Prompt-to-prompt [[Github](https://github.com/google/prompt-to-prompt/)]

**Pros and Cons**

🟢 Pros

- It could leverage foundation models to understand image content in SVG format
- Provides obvious AI performance on a cross-domain task
- Has sufficient dataset

🔴 Cons

- Generation quality has a risk of not meeting the designer's requirements since there is limited research on SVG generation
- It might be limited on generated detailed SVG components

---

### Approach #2 | New component generation
    
The system will take user input about the desired component and generate a new component based on the text prompt, which will then be interpreted by a chatGPT-like system and applied to the SVG element.

| Technology readiness | Risks | Complexity |
| ----- | ----- | ---------- |
| 🟡 Some elements are available, but further development and research needed | <div style="width: 120pt"> 🟡 Moderate risk | <div style="width: 100pt"> 🔴 Complex |


**Technologies**

- Following IconShop [[Paper](references/Research%20papers/IconShop.pdf)]. Based on a transformer-based method to achieve text-to-SVG. The dataset usage is more simple than VectorFusion.
- Following VectorFusion [[Paper](references/Research%20papers/VectorFusion.pdf)]. Prompting stable diffusion -> raster image -> pre-processing (i.e., background removal) -> vectorisation into vector image via Vectorisation [[Tutorial](https://blog.thea.codes/raster-vectorization-with-python/)][[Sample code](https://gist.github.com/theacodes/2e13e4e05700279734ca4b34df370adb)]
or Vtracer [[Github](https://github.com/visioncortex/vtracer)]

**Requirements**

- ML model: [IconShop](https://arxiv.org/pdf/2304.14400.pdf) or [VectorFusion](https://ajayj.com/vectorfusion)

<details>
<summary>Data need:</summary>

- Iconify: >150,000 open source SVG icons [[Website](https://iconify.design/)] [[Description](https://iconify.design/docs/icons/icon-data.html)] [[Figma Plug-in](https://www.figma.com/community/plugin/735098390272716381/Iconify)] [[Figma Plug-in Github](https://github.com/iconify/iconify-figma)]
    
- FIGR-8: containing **17,375 classes** of **1,548,256 images** representing pictograms, ideograms, icons, emoticons or object or conception depictions (*with both png and svg format*) [[Github](https://github.com/marcdemers/FIGR-8)]
    
    ![dataset_explanation.png](reports/figures/dataset_explanation.png)
    
- SVG Repo: with 500,000+ open-licensed SVG vector and icons [[Website](https://www.svgrepo.com/)]
            
</details>
        

**Relevant works**

[Research] 

- VectorFusion [[Paper](references/Research%20papers/VectorFusion.pdf)]: text-to-image-to-vector method
- IconShop [[Paper](references/Research%20papers/IconShop.pdf)]: The key to the success of IconShop is to exploit the sequential nature of SVG. Design a transformer-based architecture to achieve text-to-SVG.
    - with black-and-white icon dataset, [FIGR-8](https://github.com/marcdemers/FIGR-8)
- Raster-to-Vector tool: open-source model Vtracer [[Github](https://github.com/visioncortex/vtracer)]

[Business solutions]
<details>
<summary>Recraft.ai</summary>

- References: [[Website](https://www.recraft.ai/)] [[Product Hunt](https://www.producthunt.com/posts/recraft-ai?utm_source=badge-featured&utm_medium=badge&utm_souce=badge-recraft-ai)][[Demo](https://youtu.be/91_i0YcsP0o)]
- Support: (a) text prompt to svg, (b) image modification with prompt, (c) fix issues for user selected region, (d) can specify target styles
- Output format: png, jpg (512x512 & 1024x1024), SVG, Lottie
- **Try some results**: some are awesome; some are not impressive, even in the simple text prompt
    - **Awesome ones**
        
        ![Recraft - robot eating a burger (cartoon).png](reports/figures/Recraft_-_robot_eating_a_burger_(cartoon).png)
        
        ![Recraft - text prompt to svg.png](reports/figures/Recraft_-_text_prompt_to_svg.png)
        
        with complex details
        ![with complex details](reports/figures/Recraft_-_text_prompt_to_svg_with_extreme_details.png)
        
    - **Not impressive ones**
        
        ![Recraft - (complex) text prompt to svg.png](reports/figures/Recraft_-_(complex)_text_prompt_to_svg.png)
        
        Not impressive one, even in simple prompt “hand”
        
        ![Recraft_can't used results.png](reports/figures/Recraft_cant_used_results.png)
</details>

<details>
<summary>iconomy.app</summary>

- Reference: [[Try the Demo](https://run.iconomy.app/)]
- 👍 have web UI; the result is acceptable
    
    ![UI sample.png](reports/figures/UI_sample.png)
    
- 👎 no API; only 5 trys for free

</details>

- Adobe Vectorisation [[Website](https://www.adobe.com/express/feature/image/convert/svg)]



**Pros and Cons**

🟢 Pros

- Could leverage foundation models to generate decent raster image (if we choose the solution of raster-to-svg)
- Have two state-of-the-art research solutions with different generative architectures for guidance
- Have sufficient dataset

🔴 Cons

- No respective open-source Github repo available for checking the performance of the research paper
- Generation quality has the risk of not meeting the designer's requirements since there is limited research on SVG generation

---

### Approach #3 | New layout generation
    
The system will take user input about the desired layout and generate a new page based on the existing elements. The idea is to utilize a top-down approach, first generating a layout, after - populating it with elements. 

| Technology readiness | Risks | Complexity |
| ----- | ----- | ---------- |
| 🟡 Some elements are available, but further development and research needed | <div style="width: 120pt"> 🟡 Moderate risk | <div style="width: 100pt"> 🔴 Complex |

**Technology**

Pre-process SVG layouts →  Clean by place holding elements 
→ Input to LLM Model 
→ Model output high-level layout based on the prompt 
→ Post-process by replacing placeholders with SVG 
→ Output the final layout.

**Relevant works**

[Research]

- Layout generation [[Paper](references/Research%20papers/LayoutFormer++.pdf)]

- Layout generation with Transformers [[Paper](/references/Research%20papers/GUILGET.pdf)]

[Business solutions]

- Galileo AI · Copilot for interface design [[Website](https://www.usegalileo.ai/)]

- WireGen - AI GPT wireframe generation [[Figma Plug-in](https://www.figma.com/community/plugin/1221144015267698736/WireGen---AI-GPT-wireframe-generation)]

- Builder.io - Generate designs with AI & export to code [[Figma Plug-in](https://www.figma.com/community/plugin/747985167520967365/Builder.io---Generate-designs-with-AI-&-export-to-code/Builder.io---Generate-designs-with-AI-&-export-to-code)]

**Pros and Cons**

🟢 Pros

- The ability to generate new layouts based on user inputs and existing elements allows for highly adaptive and custom designs
- The model generates a high-level layout based on the prompt, which would save computation cost and time for outputting full-length SVG with content.

🔴 Cons

- No respective open-source Github repo is available for checking the performance of the research paper
- Generation quality has the risk of not meeting the designer's requirements since there is limited research on SVG generation

---

## 🏁 Final recommendation

[A1] **Editing SVG elements** using a language model appears more feasible in the short term. On the other hand, [A3] **New layout generation** could potentially demonstrate higher effectiveness for the clients; however, the lack of research and existing methods may negatively influence the complexity of its potential implementation. Besides, [A2] **New component generation** with 2 suggested implementation processes is more complex.

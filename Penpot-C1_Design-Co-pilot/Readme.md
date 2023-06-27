# Idea #1 | Design Co-pilot

## 🔎 Idea overview

Designers create the design and design system, and the co-pilot can do routine tasks such as transferring this design to other pages where you don’t need to be creative just transfer this design. So you can act like a junior designer creating content based on created design. It leaves control to the designer but can augment and scale the activities.

## 💡 Feature analysis
- **Approach #1 | Editing SVG elements**
    
    The system will allow users to edit the SVG UI elements by describing their desired changes in a text format, which will then be interpreted by a chatGPT-like system and applied to the SVG element.
    
    **Technology readiness**
    
    🟢 Ready for implementation
    
    **Risks**
    
    🟡 Moderate risk
    
    **Complexity**
    
    🟠 Moderately complex
    
    **Technologies**
    
    Following [LLM for SVG editing](https://arxiv.org/pdf/2306.06094.pdf) paper, the input can be an optimized SVG with text instructions to edit it. The language Model can be tuned on the created target dataset using raster-to-vector tools. 
    
    🖼️ **Visualization**
    
    Demo #1
    
    ![截圖 2023-06-22 上午1.55.07.png](figures/SVGEditDemo1.png)
    
    Demo #2
    
    ![截圖 2023-06-22 上午1.55.33.png](figures/SVGEditDemo2.png)
    
    Demo #3
    
    ![截圖 2023-06-22 上午1.55.40.png](figures/SVGEditDemo3.png)
    
    **Requirements**
    
    - ML model: LLM
    - [SVG optimizer](https://github.com/svg/svgo)
    - Raster-to-vector tool:
        - [[vectorisation](https://blog.thea.codes/raster-vectorization-with-python/)][[sample code](https://gist.github.com/theacodes/2e13e4e05700279734ca4b34df370adb)]
        - https://github.com/visioncortex/vtracer
    - Input: SVG component + text prompt
    - Output: edited SVG component
    - Dataset:
        - SVG components with text description for finetuning LLM
            - Iconify: >150,000 open source SVG icons
                
                [Iconify](https://iconify.design/docs/icons/icon-data.html)
                
                [Iconify](https://iconify.design/)
                
                [Iconify](https://www.figma.com/community/plugin/735098390272716381/Iconify)
                
                [https://github.com/iconify/iconify-figma](https://github.com/iconify/iconify-figma)
                
            - FIGR-8: containing **17,375 classes** of **1,548,256 images** representing pictograms, ideograms, icons, emoticons or object or conception depictions (*with both png and svg format*)
                
                [https://github.com/marcdemers/FIGR-8](https://github.com/marcdemers/FIGR-8)
                
                ![dataset_explanation.png](figures/dataset_explanation.png)
                
            - SVG Repo: with 500,000+ open-licensed SVG vector and icons
                
                [SVG Repo - Free SVG Vectors and Icons](https://www.svgrepo.com/)
                
    
    **Relevant works**
    
    [Research]
    
    [LLM for SVG editing](https://arxiv.org/pdf/2306.06094.pdf)
    
    [LLM for image editing](https://github.com/IDEA-Research/GroundingDINO/blob/main/demo/image_editing_with_groundingdino_gligen.ipynb): https://github.com/IDEA-Research/GroundingDINO + https://github.com/gligen/GLIGEN
    
    Text prompt for image editing: https://github.com/timothybrooks/instruct-pix2pix；https://github.com/google/prompt-to-prompt/
    
    **Pros and Cons**
    
    🟢 Pros
    
    - It could leverage foundation models to understand image content in SVG format
    - Provides obvious AI performance on a cross-domain task
    - Has sufficient dataset
    
    🔴 Cons
    
    - Generation quality has a risk of not meeting the designer's requirements since there is limited research on SVG generation
    - It might be limited on generated detailed SVG components

- **Approach #2 | New component generation**
    
    The system will take user input about the desired component and generate a new component based on the text prompt, which will then be interpreted by a chatGPT-like system and applied to the SVG element.
    
    **Technology readiness**
    
    🟡 Some elements are available, but further development and research needed
    
    **Risks**
    
    🟡 Moderate risk
    
    **Complexity**
    
    🔴 Complex
    
    **Technologies**
    
    - Following [IconShop](https://arxiv.org/pdf/2304.14400.pdf) paper. Based on a transformer-based method to achieve text-to-SVG. The dataset usage is more simple than VectorFusion.
    - Following [VectorFusion](https://ajayj.com/vectorfusion) paper. Prompting stable diffusion -> raster image -> pre-processing (i.e. background removal) -> vectorisation into vector image [[vectorisation](https://blog.thea.codes/raster-vectorization-with-python/)][[sample code](https://gist.github.com/theacodes/2e13e4e05700279734ca4b34df370adb)]/https://github.com/visioncortex/vtracer
    
    **Requirements**
    
    - ML model: [IconShop](https://arxiv.org/pdf/2304.14400.pdf) or [VectorFusion](https://ajayj.com/vectorfusion)
    - Data need:
        - Iconify: >150,000 open source SVG icons
            
            [Iconify](https://iconify.design/docs/icons/icon-data.html)
            
            [Iconify](https://iconify.design/)
            
            [Iconify](https://www.figma.com/community/plugin/735098390272716381/Iconify)
            
            [https://github.com/iconify/iconify-figma](https://github.com/iconify/iconify-figma)
            
        - FIGR-8: containing **17,375 classes** of **1,548,256 images** representing pictograms, ideograms, icons, emoticons or object or conception depictions (*with both png and svg format*)
            
            [https://github.com/marcdemers/FIGR-8](https://github.com/marcdemers/FIGR-8)
            
            ![dataset_explanation.png](figures/dataset_explanation.png)
            
        - SVG Repo: with 500,000+ open-licensed SVG vector and icons
            
            [SVG Repo - Free SVG Vectors and Icons](https://www.svgrepo.com/)
            
    
    **Relevant works**
    
    [Research] 
    
    - [VectorFusion](https://ajayj.com/vectorfusion): text-to-image-to-vector method
    - [IconShop](https://arxiv.org/pdf/2304.14400.pdf): The key to the success of IconShop is to exploit the sequential nature of SVG. Design a transformer-based architecture to achieve text-to-SVG.
        - with black-and-white icon dataset, [FIGR-8](https://github.com/marcdemers/FIGR-8)
    - Raster-to-Vector: open-source model https://github.com/visioncortex/vtracer
    
    [Business solutions]
    
    - [Recraft.ai](https://www.recraft.ai/) [[Product Hunt](https://www.producthunt.com/posts/recraft-ai?utm_source=badge-featured&utm_medium=badge&utm_souce=badge-recraft-ai)][[Demo](https://youtu.be/91_i0YcsP0o)]: (a) text prompt to svg, (b) image modification with prompt, (c) fix issues for user selected region, (d) can specify target styles
        - Output format: png, jpg (512x512 & 1024x1024), SVG, Lottie
        - **Try some results**: some are awesome; some are not impressive, even in the simple text prompt
            - **Awesome ones**
                
                ![Recraft - robot eating a burger (cartoon).png](figures/Recraft_-_robot_eating_a_burger_(cartoon).png)
                
                ![Recraft - text prompt to svg.png](figures/Recraft_-_text_prompt_to_svg.png)
                
                ![with complex details](figures/Recraft_-_text_prompt_to_svg_with_extreme_details.png)
                
                with complex details
                
            - **Not impressive ones**
                
                ![Recraft - (complex) text prompt to svg.png](figures/Recraft_-_(complex)_text_prompt_to_svg.png)
                
                Not impressive one, even in simple prompt “hand”
                
                ![Recraft.ai_can't used results.png](figures/Recraft_cant_used_results.png)
                
    - [iconomy.app](https://run.iconomy.app/)
        - 👍 have web UI; the result is acceptable
            
            ![UI sample.png](figures/UI_sample.png)
            
        - 👎 not have API; only 5 try for free
    - [Adobe Vectorisation](https://www.adobe.com/express/feature/image/convert/svg)
    
    **Pros and Cons**
    
    🟢 Pros
    
    - Could leverage foundation models to generate decent raster image (if we choose the solution of raster-to-svg)
    - Have two state-of-the-art research solutions with different generative architectures for guidance
    - Have sufficient dataset
    
    🔴 Cons
    
    - No respective open-source Github repo available for checking the performance of the research paper
    - Generation quality has the risk of not meeting the designer's requirements since there is limited research on SVG generation

- **Approach #3 | New layout generation**
    
    The system will take user input about the desired layout and generate a new page based on the existing elements. The idea is to utilize a top-down approach, first generating a layout, after - populating it with elements. 
    
    **Technology readiness**
    
    🟡 Some elements are available, but further development and research needed
    
    **Risks**
    
    🟡 Moderate risk
    
    **Complexity**
    
    🔴 Complex
    
    **Technology**
    
    Pre-process SVG layouts →  Clean by place holding elements 
    → Input to LLM Model 
    → Model output high-level layout based on the prompt 
    → Post-process by replacing placeholders with SVG 
    → Output the final layout.
    
    **Relevant works**
    
    [Research]
    
    - [Layout generation](https://openaccess.thecvf.com/content/CVPR2023/papers/Jiang_LayoutFormer_Conditional_Graphic_Layout_Generation_via_Constraint_Serialization_and_Decoding_CVPR_2023_paper.pdf)
    - [Layout generation with Transformers](https://arxiv.org/pdf/2304.09012.pdf)
    
    [Business solutions]
    
    [Galileo AI · Copilot for interface design](https://www.usegalileo.ai/)
    
    [WireGen - AI GPT wireframe generation](https://www.figma.com/community/plugin/1221144015267698736/WireGen---AI-GPT-wireframe-generation)
    
    [Figma](https://www.figma.com/community/plugin/747985167520967365/Builder.io---Generate-designs-with-AI-&-export-to-code/Builder.io---Generate-designs-with-AI-&-export-to-code)
    
    **Pros and Cons**
    
    🟢 Pros
    
    - The ability to generate new layouts based on user inputs and existing elements allows for highly adaptive and custom designs
    - The model generates a high-level layout based on the prompt, which would save computation cost and time for outputting full-length SVG with content.
    
    🔴 Cons
    
    - No respective open-source Github repo is available for checking the performance of the research paper
    - Generation quality has the risk of not meeting the designer's requirements since there is limited research on SVG generation


## 🏁 Final recommendation

[A1] **Editing SVG elements** using a language model appears more feasible in the short term. On the other hand, [A3] **New layout generation** could potentially demonstrate higher effectiveness for the clients; however, the lack of research and existing methods may negatively influence the complexity of its potential implementation. Besides, [A2] **New component generation** with 2 suggested implementation processes is more complex.


Suggested Project Organization
------------

    ├── LICENSE
    ├── Makefile           <- Makefile with commands like `make data` or `make train`
    ├── README.md          <- The top-level README for developers using this project.
    ├── data
    │   ├── external       <- Data from third party sources.
    │   ├── interim        <- Intermediate data that has been transformed.
    │   ├── processed      <- The final, canonical data sets for modeling.
    │   └── raw            <- The original, immutable data dump.
    │
    ├── docs               <- A default Sphinx project; see sphinx-doc.org for details
    │
    ├── models             <- Trained and serialized models, model predictions, or model summaries
    │
    ├── notebooks          <- Jupyter notebooks. Naming convention is a number (for ordering),
    │                         the creator's initials, and a short `-` delimited description, e.g.
    │                         `1.0-jqp-initial-data-exploration`.
    │
    ├── references         <- Data dictionaries, manuals, and all other explanatory materials.
    │
    ├── reports            <- Generated analysis as HTML, PDF, LaTeX, etc.
    │   └── figures        <- Generated graphics and figures to be used in reporting
    │
    ├── requirements.txt   <- The requirements file for reproducing the analysis environment, e.g.
    │                         generated with `pip freeze > requirements.txt`
    │
    ├── setup.py           <- makes project pip installable (pip install -e .) so src can be imported
    ├── src                <- Source code for use in this project.
    │   ├── __init__.py    <- Makes src a Python module
    │   │
    │   ├── data           <- Scripts to download or generate data
    │   │   └── make_dataset.py
    │   │
    │   ├── features       <- Scripts to turn raw data into features for modeling
    │   │   └── build_features.py
    │   │
    │   ├── models         <- Scripts to train models and then use trained models to make
    │   │   │                 predictions
    │   │   ├── predict_model.py
    │   │   └── train_model.py
    │   │
    │   └── visualization  <- Scripts to create exploratory and results oriented visualizations
    │       └── visualize.py
    │
    └── tox.ini            <- tox file with settings for running tox; see tox.readthedocs.io


--------

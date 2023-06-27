# Idea #1 | Design Co-pilot

## 🔎 Idea overview

Designers create the design and design system, and the co-pilot can do routine tasks such as transferring this design to other pages where you don’t need to be creative just transfer this design. So you can act like a junior designer creating content based on created design. It leaves control to the designer but can augment and scale the activities.

<br>

## 💡 Feature analysis
### Approach #1 | Editing SVG elements [[More](Approach#1-Editing_SVG_Elements/Readme.md)]

The system will allow users to edit the SVG UI elements by describing their desired changes in a text format, which will then be interpreted by a chatGPT-like system and applied to the SVG element.

### Approach #2 | New component generation [[More](Approach#2-New_Component_Generation/Readme.md)]
    
The system will take user input about the desired component and generate a new component based on the text prompt, which will then be interpreted by a chatGPT-like system and applied to the SVG element.

### Approach #3 | New layout generation [[More](Approach#3-New_Layout_Generation/Readme.md)]
    
The system will take user input about the desired layout and generate a new page based on the existing elements. The idea is to utilize a top-down approach, first generating a layout, after - populating it with elements. 

<br>

## 🏁 Final recommendation

[A1] **Editing SVG elements** using a language model appears more feasible in the short term. On the other hand, [A3] **New layout generation** could potentially demonstrate higher effectiveness for the clients; however, the lack of research and existing methods may negatively influence the complexity of its potential implementation. Besides, [A2] **New component generation** with 2 suggested implementation processes is more complex.

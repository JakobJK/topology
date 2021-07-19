---
layout: '../layout/Main.astro'
---

# modelChecker

Within Maya there is not a simple native way of verifying that your geometry meets all of the technical requirements to satisfy every aspect of the production pipeline. When you are working at a studio, they will undoubtly have their own tools in place to verify their needs. When I went freelancing, I decided to write the modelChecker python tool. Having to rely on verifying by hand is incredibly error prone. modelChecker aims to be as unopinionated as possible, while covering most of the expected needs of geometry for most pipelines.

![modelChecker](assets/modelChecker.jpeg)

## Setup

Place the modelChecker files in your maya scripts directory and create a python shell button with the following code:

```python
from modelChecker_UI import modelCheckerUI

modelCheckerUI.show_UI()
```

## Usage

There are three ways to run the checks.

1. If you have objects selected the checks will run on the current selection.
2. A hierachy by declaring a top node in the UI.
3. If you have an empty selection and no top node is declared the checks will run on the entire scene.

The documentation will refer to the nodes you are running checks on as your "declared nodes", to not be confused with your active selection.

Important! Your current selection will have prioirtiy over the top node defined in the UI. The reason is to be able to quickly debug errror nodes.

## Checks

Here is an extensive lists of all of the checks the modelChecker can make on your 3d models. Passing all checks does not inherently make for a good model. Understand what is required for your production will.

## Naming

<details>
<summary>duplicatedNames</summary>
<p>
  Returns any node within the hierachy that is not uniquely named
</p>
</details>

<details>
<summary>shapeNames</summary>
Returns shape nodes which does not follow the naming convention of transformNode+"Shape"
</details>

<details>
<summary>namespaces</summary>
<p>
  Returns nodes that are not in the global name space</p>
  </details>

## Topology

<details>
<summary>triangles</summary>

<p>Will return a list of traingles</p>
</details>
<details>
<summary>ngons</summary>
<p>
Will return a list of Ngons
</p>
</details>
<details>
<summary>openEdges</summary>
<p>
Will return any Edge that is connected to onyl one face
</p>
</details>
<details>
<summary>hardEdges</summary>
<p>
Will return any edges that does not have softened normals
</p>
</details>
<details>
<summary>lamina</summary>
<p>
  Returns lamina faces
</p>
</details>
<details>
  <summary>zeroAreaFaces</summary>
    Returns
</details>
<details>
<summary>zeroLengthEdges</summary>
    Returns edges which has a length less than 0.000001 units
</details>
<details>
<summary>noneManifoldEdges</summary>
</details>
<details>
<summary>starlike</summary>
</details>

## UVs

<details>
<summary>selfPenetratingUVs</summary>
</details>
<details>
<summary>missingUVs</summary>
<p>
Returns any polygon object that does have UVs
</p>
</details>
<details>
<summary>uvRange</summary>
</details>
<details>
<summary>crossBorder</summary>
</details>

## General

<details>
<summary>layers</summary>
</details>
<details>
<summary>history</summary>
</details>
<details>
<summary>shaders</summary>
</details>
<details>
<summary>unfrozenTransforms</summary>
</details>
<details>
<summary>uncenteredPivots</summary>
</details>
<details>
<summary>parentGeometry</summary>
</details>
<details>
<summary>emptyGroups</summary>
</details>

## Authors

- [**Jakob Kousholt**](https://www.linkedin.com/in/jakejk/) - Software Engineer / Freelance Creature Modeler
- [**Niels Peter Kaagaard**](https://www.linkedin.com/in/niels-peter-kaagaard-146b8a13) - Modeler at Weta Digital

## License

modelChecker is licensed under the [MIT](https://rem.mit-license.org/) License.

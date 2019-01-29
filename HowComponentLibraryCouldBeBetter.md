# Component Library

## Purpose:

- Pre-agreed that both designers and developers use Component Library.
- No Designer/Developer should spend the time creating their own "Button".
  - More time for Developer/Designer to spend on more important/difficult tasks.
- One source of truth for uniformity sitewide.
- Better/easier experience as a Developer/Designer.
- Open source - everyone should be a contributer to Component Library.

## The Problem:

- No one really seems to be using it...
  - Those who are, use it reluctantly.
  - Those who aren't, are spending time making their own "Button".
- There are multiple versions across the site and thanks to global css, other versions from other teams can override your version.
  - The solution of most Developers... don't use Component Library.
- Very difficult to use:
  - Components are not well documented.
  - CL layout makes it hard to find what components exist or if there is an update for an existing component.
  - In some instances, there is documentation for things that don't exist in CL.
  - Many developers opt out of using CL because "I can do it faster myself".
- Codebase is unnecessarily over complex.
  - So many nonsense scripts.
  - Poor naming conventions.
  - Poor file/folder structure.
  - Work has to be coded twice:
    - Once for CL and once for docs.
  - Poor documentation on how to work a dev server or how to contribute.
  - Not properly maintained and kept up to date (using webpack v2 and babel v6 with preset es2015).
  - Currently using Rollup, which isn't even to v1 yet (did an architect approve this?).
  - Most components destruct from props then spread all props afterward.
    - This means that the developer can only replace and override CL, while not having the ability to extend **ONLY IF NEEDED**.

  ```javascript
  const Component = props => {
    const { weight } = props;

    return <component className='myClass' weight={weight} {...props} />;
  };
  ```

## The Goal/Solution:

- CL should be so intuitive and so well documented that a Developer would have a harder time "doing it themselves".
  - Documentation should clearly show available options, how they work, and the required props to use them.
  - Move to a different css system so you no longer have to import styles separately.
  - Give Developers the abilty to "extend" CL **ONLY IF NEEDED**.
    - this is necessary in the **RARE** case where the styles are off because of parent styling, browser styling, or some other **RARE** case that the developer needs to change something.
    - This is to remove the "I'll just build it myself" mentallity.
  - Change imports to be more intuitive.
  
  (**I noticed this fixed when I recently used it** `import Button from 'overstock-component-library/lib/Button';`)

    - should be
    ```javascript
    import Button from 'componentLibrary/Button';
    ```
    - not
    ```javascript
    import Button from 'componentLibrary/lib/buttons/Button';
    ```
- Move to CSS-modules so that css versioning won't have an affect across different teams.
- Simplify Code Base.

  - Anyone should have the ability to contribute to CL.
  - Developer experience should be enjoyable and the learning curve should be low.
  - Increase documentation so that other developers can get up and running fast and contribute more to CL.
    - This means higher quality and quantity of components available from CL.
    - A true design system that people can understand and have a greater abilty to use because we all built it as a community/business/**team**.
  - Explore moving to TypeScript.

    - Better editor tooling.
    - Type system that is made for catching errors faster.
    - Explicitly define props to make components much easier to use.
      ![alt text](./typescriptexp.png)

  - "Busy is the new stupid." (**maybe mention who said this?**) 
    - Complex _busy_ code, **does not** mean better.

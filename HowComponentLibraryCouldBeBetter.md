# Component Library

## Purpose:

- Pre-agreed that both designers and developers use Component Library (CL).
- No Designer/Developer should spend the time creating their own "Button".
  - More time for Developer/Designer to spend on more important/difficult tasks.
- One source of truth for uniformity sitewide.
- Better/easier experience as a Developer/Designer
- Open source - everyone should be a contributer to Component Library.

## The Problem:

- No one seems to be using it:
  - Those who are, use it reluctantly.
  - Those who aren't, are spending time making their own "Button".
- Multiple versions across the site, and due to global css, other versions from other teams override your version.
  - The solution most Developers are taking to this: don't use Component Library.
- Very difficult to use:
  - Components are not well documented.
  - Layout makes it hard to find if CL has component or updated component.
  - What is documented, isn't what is really in CL.
  - Many developers opt out of using CL because "I can do it faster myself".
- Codebase is unnecessarily complex:
  - Many scripts that do nonsense.
  - Poor naming conventions.
  - Poor file/folder structure.
  - Work has to be coded twice.
    - once for CL and once for docs
  - Poor documentation on how to work dev server or contribute.
  - Not properly maintained and kept up to date (ex. using webpack v2 and babel v6 with preset es2015).
  - Currently using Rollup???, (which isn't even to v1 yet...).
  - Most components destruct from props then spread all props afterward.
    - this means that the Dev can only replace and override CL and does not have ability to extend **ONLY IF NEEDED**.

  ```javascript
  const Component = props => {
    const { weight } = props;

    return <component className='myClass' weight={weight} {...props} />;
  };
  ```

## The Goal/Solution:

- CL should be intuitive and well documented so a Developer would have a harder time "doing it themselves".
  - Documentation should clearly show available options, as well as how they work and the required props to use them.
  - Moving to a different css system so you no longer have to import styles separately.
  - Give Developers the abilty to "extend" CL **ONLY IF NEEDED**.
    - this is necessary in the **RARE** case that the developer needs to change something i.e styles are off due to parent styling or browser styling etc.
    - This is to remove the "I'll just build it myself" mentality.
  - Change imports to be more intuitive.
    - should be
    ```javascript
    import Button from 'componentLibrary/Button';
    ```
    - not
    ```javascript
    import Button from 'componentLibrary/lib/buttons/Button';
    ```
- Start moving to CSS-modules so CSS versioning won't have an effect across different teams.
- Simplify Code Base.
  - Anyone should have the ability to contribute to CL.
  - Developer Experience should be enjoyable and learning curve should be low.
  - Increase documentation so other devs can get up and running quickly and contribute more to CL.
    - This means increased quality and quantity of components available from CL.
    - A true design system that people can understand and have a greater abilty to use -- because we all built it as a community/business/**team**
  - Explore moving to TypeScript.
    - Better editor tooling.
    - Type system made for catching errors faster.
    - Explicitly define props to make components much easier to use.
      ![alt text](./typescriptexp.png)

  - "Busy is the new stupid"
    - Complex _busy_ code, **does not** mean better.

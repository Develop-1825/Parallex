# Overlap shunte hi samajh jana ki absolute positioning use karna hai.

## Good Practise

- Always maintain everything inside a wrapper class.
- Wrapper class is nothing but a outer div container inside which we do all the work.

# overflow-x,overflow-y

- Handles scrolling in horizontal and vertical movement.

# **Whenever you want to work on z-axis / 3d, the very first step should be turning on the perspective.**

- Give any value to perspective,just turn on. `perspective : 10px;` in wrapper.

# Whenever you want to add **3d effect** , add `transform-style : preserve-3d` to that class.

# z-index

- The z-index property in CSS controls the vertical stacking order of elements that overlap. This property determines which element will appear in front of or behind other elements.

  Key Concepts:
  Stacking Context:

  A stacking context is a three-dimensional conceptualization of HTML elements along the z-axis. Elements that have a z-index are placed on different "layers" along this axis.
  The root stacking context is the entire webpage. New stacking contexts are created by elements with certain properties, such as position: relative;, position: absolute;, position: fixed;, position: sticky;, and when z-index is set to a value other than auto.
  Positioned Elements:

  For z-index to have an effect, the element must be positioned. This means it must have a position value of relative, absolute, fixed, or sticky.
  Elements that aren't positioned (position: static;, the default) do not respect z-index and will appear in the order they are in the HTML document (source order).
  z-index Values:

  Positive Values (e.g., z-index: 1;, z-index: 10;): Elements with higher z-index values are stacked on top of elements with lower values.
  Negative Values (e.g., z-index: -1;): Elements with negative z-index values are stacked behind elements with higher values.
  z-index: auto;: The element does not create a new stacking context and will be positioned according to its order in the document and the stacking context it is in.
  Stacking Order:

  Elements with the same z-index are stacked according to their position in the HTML document. Elements defined later in the document are stacked on top of those defined earlier.
  Within a stacking context, elements with a higher z-index value will appear above those with a lower z-index value.
  Key Takeaway:
  The z-index property allows you to control the stacking order of overlapping elements. It is crucial for managing complex layouts where multiple layers of content need to overlap and interact in a specific way.

# EG :

- Given your code:

  html
  Copy code

    <div class="container">
        <img src="./background.png" alt="background" class="background">
        <img src="./foreground.png" alt="foreground" class="foreground">
        <h1>ADVENTURE</h1>
    </div>
    Explanation of Default Stacking Context:
    No Explicit z-index:

  Since no z-index values are specified, all elements will have their z-index set to auto. This means the elements will be stacked according to the natural flow of the document and the order in which they appear in the HTML.
  Stacking Order:

  **Elements are stacked from bottom to top based on their order in the HTML**:
  The first element (<img src="./background.png" class="background">) will be at the bottom.
  The second element (<img src="./foreground.png" class="foreground">) will be stacked above the first.
  The third element (<h1>ADVENTURE</h1>) will be stacked above both images.
  Resulting Display:

  background image: This image will be at the bottom layer.
  foreground image: This image will be on the middle layer, above the background image.
  h1 text ("ADVENTURE"): The text will be on the top layer, above both images.
  Visual Representation:
  Layer 1 (Bottom): background image.
  Layer 2 (Middle): foreground image.
  Layer 3 (Top): h1 text.

# transform-style : preserve-3d;

- The CSS property transform-style: preserve-3d; is used in 3D transformations to maintain the 3D positioning of child elements. When you apply transform-style: preserve-3d; to a parent element, any 3D transforms applied to its children are preserved, and the children are rendered in the 3D space relative to the parent.

  Explanation with Your Example:
  Given your original code:

  html
  Copy code

    <div class="container">
        <img src="./background.png" alt="background" class="background">
        <img src="./foreground.png" alt="foreground" class="foreground">
        <h1>ADVENTURE</h1>
    </div>
    If you were to use transform-style: preserve-3d; on the .container and apply 3D transformations to the children, the 3D effects would be preserved and the children would appear in 3D space relative to the parent .container.

# object-fit : cover;

- fits the image inside the container.

In the context of CSS and positioning, "translation" refers to the movement or shifting of an element from its original position along one or more axes (X, Y, or Z) without affecting its surrounding elements or changing its position in the document flow.

# transform: translateZ(-30px) scale(3.5);

- First image is translated/ shift 30 px away from the viewer which makes it look small, then, we scale it up by 3.5 times to fit the screen

# background-image : url(path)

- this is another way to add image to a class using css

## **Interview Question**

- why use background-image instead of img tag?

  - Both the `<img>` tag and the `background-image` CSS property are used to display images on a web page, but they serve different purposes and have distinct use cases. Here’s a comparison to understand when to use each:

    ### `<img>` Tag

    **Advantages**:

    1. **Semantic HTML**:

    - Provides meaningful content and structure, which is beneficial for accessibility and SEO. It allows for attributes like `alt` for alternative text, which helps screen readers understand the image’s content.

    2. **Responsiveness**:

    - Easily adapted with responsive techniques like `srcset` and `sizes`, allowing for different image resolutions based on the viewport size.

    3. **Loading Behavior**:

    - Images are treated as content and can be lazy-loaded to improve performance, especially if the image is not immediately visible.

    4. **Image Attributes**:

    - Supports attributes like `width`, `height`, and `srcset` for specifying multiple image sources for different devices and resolutions.

    **Example**:

    ```html
    <img src="logo.png" alt="Company Logo" width="200" height="100" />
    ```

    ### `background-image` CSS Property

    **Advantages**:

    1. **Design Flexibility**:

    - Allows for more flexible and complex designs, such as multiple backgrounds, background positioning, and layering. You can also use CSS to control how the background image is displayed, such as with `background-size`, `background-repeat`, and `background-position`.

    2. **Overlays and Effects**:

    - Background images can be combined with other CSS properties (e.g., `background-blend-mode`, gradients) to create effects that are not possible with the `<img>` tag alone.

    3. **Non-Content Elements**:

    - Ideal for decorative images that are part of the design rather than content. For instance, background patterns, images behind text, and layout graphics.

    4. **Dynamic Backgrounds**:

    - Allows for setting backgrounds dynamically via CSS without changing the HTML structure. Useful for adding backgrounds to elements like divs, sections, or containers.

    **Example**:

    ```css
    .container {
      background-image: url("pattern.png");
      background-size: cover;
      background-repeat: no-repeat;
    }
    ```

    ### Use Cases:

    - **Use `<img>`**:

      - When the image is a meaningful part of the content (e.g., product images, profile pictures).
      - When accessibility and SEO are priorities.
      - When you need to control the image’s dimensions, aspect ratio, and source for different devices.

    - **Use `background-image`**:
      - When the image is purely decorative or used for layout purposes (e.g., background patterns, decorative effects).
      - When you need to overlay text or other elements on top of the image.
      - When you need advanced styling options that aren’t possible with `<img>` (e.g., background positioning, blending).

    In summary, the choice between using `<img>` and `background-image` depends on whether the image is part of the content or purely a design element.

# background-attachment: fixed;

- The element remains fixed and everything scrolls above it.
- Basically we fic it to the background.

# background-position: center;

- positions the background image to center.

# background-size: cover;

- fits image to the container size. Because sometimes the image is too big for the screen to render properly,some part of the image might go trimmed.

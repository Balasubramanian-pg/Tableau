Here is the crux of the Tableau Embedding API for React in a 3-minute summary.

### 1. Installation
Install the package via npm. **Crucial:** Ensure the version matches the Tableau Server/Cloud version hosting your content.

```bash
npm i @tableau/embedding-api-react
# Or specific version: npm i @tableau/embedding-api-react@3.12.1
```

### 2. Basic Usage (Rendering a Viz)
Import the component and pass the URL to the `src` prop. You can pass other attributes (like `hideTabs` or `toolbar`) as standard React props.

```jsx
import { TableauViz } from '@tableau/embedding-api-react';

export default function MyViz() {
  return (
    <TableauViz
      src="https://your-tableau-server/views/workbook/sheet"
      toolbar="hidden"
      hideTabs
    />
  );
}
```

### 3. Accessing the API (Using Refs)
To interact with the viz programmatically (e.g., changing filters, getting sheet names) after it loads, you must use the specific **Ref hook**.

1.  Import `useTableauVizRef`.
2.  Initialize the hook (`const vizRef = useTableauVizRef()`).
3.  Pass it to the `ref` prop of the component.
4.  Access the API via `vizRef.current`.

```jsx
import { TableauViz, useTableauVizRef } from '@tableau/embedding-api-react';

export default function MyViz() {
  const vizRef = useTableauVizRef();

  const handleButton = () => {
    // Access the underlying API object
    console.log(vizRef.current.workbook.activeSheet.name); 
  };

  return (
    <>
      <button onClick={handleButton}>Log Sheet Name</button>
      <TableauViz ref={vizRef} src="..." />
    </>
  );
}
```

### 4. Event Handling
To listen for events (like selection changes or when the viz becomes interactive), use the **Callback hooks**. These are wrappers around `useCallback` to prevent unnecessary re-renders.

1.  Import the specific hook (e.g., `useTableauVizFirstInteractiveCallback`).
2.  Define the callback (pass an empty dependency array `[]` to run it once).
3.  Pass it to the corresponding prop (e.g., `onFirstInteractive`).

```jsx
import { TableauViz, useTableauVizFirstInteractiveCallback } from '@tableau/embedding-api-react';

export default function MyViz() {
  // Event Handler
  const onVizReady = useTableauVizFirstInteractiveCallback((event) => {
    console.log("Viz is loaded!", event.target);
  }, []);

  return (
    <TableauViz 
      src="..." 
      onFirstInteractive={onVizReady} 
    />
  );
}
```

### 5. Available Components
The library provides three main components, each with its own set of Ref and Event hooks:

*   **`<TableauViz>`**: For embedding standard dashboards/views.
*   **`<TableauAuthoringViz>`**: For embedding the Web Edit experience.
*   **`<TableauPulse>`**: For embedding Tableau Pulse metrics.

### Key Gotchas
*   **ES Modules:** If your project isn't set up for modules, ensure `"type": "module"` is in your `package.json`.
*   **Import `Api`:** If you need non-component classes, you can import `Api` directly from this package (it is a re-export of `@tableau/embedding-api`).

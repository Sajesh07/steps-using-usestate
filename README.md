## Steps Using useState (React Demo)

An educational React example showing how to manage UI state with `useState`. It demonstrates a simple multi-step UI with a "Previous" and "Next" flow and a toggle to show/hide the steps.

### How it works

- **State**: The components track `step` (1 → 3) and `isOpen` (show/hide panel) using `useState`.
- **Next button re-render**: Clicking "Next" calls `setStep(s => s + 1)` while `step < 3`. Any state update triggers React to re-render the parts of the UI that read `step` (the active number indicators and the step message). When `step` is already 3, clicking "Next" does nothing and there is no re-render because state doesn't change.
- **Previous button**: Decreases `step` while `step > 1` and re-renders accordingly.
- **Close (×) button**: Toggles `isOpen`, conditionally rendering the steps panel.

Key spots in code:

- `src/App-v1.js`: Inline buttons and logic in a single component.
- `src/App.js`: A variant that splits UI into `Steps`, `StepMessage`, and `Button` components.

### Prerequisites

- Node.js 18+ recommended

### Install

```bash
npm install
```

### Run the app (development)

```bash
npm start
```

Then open `http://localhost:3000` in your browser.

### Build for production

```bash
npm run build
```

### Project structure

```
public/
  index.html
src/
  App.js        # Main demo with useState for step + isOpen
  App-v1.js     # Componentized variant (Steps, StepMessage, Button)
  index.js      # React entry point
  index.css     # Basic styles for steps and buttons
```

### What to look for

- How `setStep` and `setIsOpen` cause re-renders by changing state.
- Conditional rendering with `{isOpen && (...)}`.
- Deriving UI from state: active step indicators and `messages[step - 1]`.

### Children props

- `StepMessage` accepts `children` and renders whatever is passed between its tags.

Usage in `src/App.js`:

```13:20:src/App.js
      <StepMessage step={1}>
        <p>Pass in content</p>
        <p>✌️</p>
      </StepMessage>
```

Definition in `src/App.js`:

```90:96:src/App.js
function StepMessage({ step, children }) {
  return (
    <div className="message">
      <h3>Step {step}</h3>
      {children}
    </div>
  );
}
```

### Common tweaks

- Change the number of steps by adjusting the `messages` array and the max/min checks around `step`.
- Style updates in `src/index.css`.

### License

MIT

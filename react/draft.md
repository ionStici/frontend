# Thinking in React

## State Management

**Local State:** State needed only by one or few components. State that is defined in a component and only that component and child components have access to it (by passing via props).

**Global State:** State that many components might need. Shared state that is accessible to every component in the entire application. Tools for managing global state: Context API & Redux.

**Derived State:** state that is computed from an existing piece of state or from props.

<br>

## Lifting State Up

**Lifting State Up:** whenever multiple sibling components need access to the same state, we move that piece of state up to the first common parent component.

```jsx
function App() {
  const [items, setItems] = useState([]);

  const handleAddItems = (item) => {
    setItems((prev) => [...prev, item]);
  };

  return (
    <>
      <Form onAddItems={handleAddItems} />
      <Items items={items} />
    </>
  );
}

function Form({ onAddItems }) {
  const input = useRef(null);

  const handleClick = () => {
    onAddItems(input.current.value);
  };

  return (
    <>
      <input type="text" ref={input} />
      <button>Click</button>
    </>
  );
}

function Items({ items }) {
  return <p>{items.join(" ")}</p>;
}
```

<br>

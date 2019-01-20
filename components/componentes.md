# Styling

## Styling React Components

### Theming

A través de un ThemeProvider facilito a los componentes la configuración del tema.

```jsx
const Button = styled.button`
    border: 1px solid ${props => props.theme.main};
    border-radius: 3px;
`
const theme = { main: 'green' }
render(
    <ThemeProvider theme={theme}>
        <Button>Themed</Button>
    </ThemeProvider>
)
```

### Style customization

A través de propiedades facilito inyectar nuevos estilos al componente

```jsx
const Button = styled.button`
    border: 1px solid red;
    border-radius: 3px;
    ${props => props.styles};
`
const newStyles = css`
    color: black;
    background-color: ${props => props.primary ? 'blue' : undefined)};
`
render(
    <Button styles={styles}>
        Customized button
    </Button>
)
```

Para componentes mas complejos podemos permitir recibir los estilos de cada uno de los componentes individuales de su interior

```jsx
const Counter = ({ children, styles }) => (
    <Wrapper styles={styles.Wrapper}>
        <Count styles={styles.Count}>
            {children}
        </Count>
    </Wrapper>
)
const myCounter = {
    Wrapper: css`
        background: gray
    `,
    Count; css`
        color: red
    `
}
render(
    <Counter styles={myCounter}>
        132
    </Counter>
)
```

### Render customization

A través de factorías se permite inyectar los componentes específicos

```jsx
const getCounter = ({Wrapper, Count}) => (
    ({children, styles}) => (
        <Wrapper styles={styles.Wrapper}>
            <Count styles={styles.Count}>
                {children}
            </Count>
        </Wrapper>
    )
)
const Counter = getCounter({
    Wrapper: styled.div`
        background-color: red;
        width: 100px;
        ${props => props.styles};
    `,
    Count: styled.span`
        color: white;
        display: block;
        ${props => props.styles};
    `
});

```

¿Y si quisiera modificar estilos en base a el estado del componente?  
Podemos hacerlo a través de pasar a los componentes de vista parte del estado del componente de lógica a través de una función encargada de inyectar nuevas propiedades a los componentes vista con la información necesaria.

```jsx
const getCounter = ({Wrapper, Count, passthrough}) => (
    props => (
        <Wrapper 
            styles={props.styles.Wrapper} 
            {...passthrough('Wrapper', props, this}
        >
            <Count 
                styles={props.styles.Count}  
                {...passthrough('Count', props, this}
            >
                {props.children}
            </Count>
        </Wrapper>
    )
)
function passthrough(nodeName, props, instance) {
    switch(nodeName) {
        case 'Wrapper': return { counter: props.counter }
        default: return {}
    }
}
const Counter = getCounter({
    passthrough,
    Wrapper: styled.div`
        background-color: ${props => props.counter > 10 && 'red'};
        width: 100px;
        ${props => props.styles};
    `,
    Count: styled.span`
        color: white;
        display: block;
        ${props => props.styles};
    `
});
```

\[[Javi Velasco: Styling components](https://www.youtube.com/watch?v=Y1rfuMVIqOw)\]

### Recursos

* [flow typeface](%20https://danross.co/flow/): Permite crear textos para wireframes o páginas de carga/loading de forma sencilla.


# JSX

[JSX](https://facebook.github.io/jsx) is an XML-like syntax extension to ECMAScript without any defined semantics.

JSX is a JavaScript Extension Syntax used in React to easily write HTML and JavaScript together.

## 实例

Input jsx

    var hello = <h1>Hello world</h1>;
    ReactDOM.render(hello, document.getElementById('hello'));

Converted javascript

    var hello = React.createElement(
        'h1',
        null,
        'Hello world'
    );
    ReactDOM.render(hello, document.getElementById('hello'));

## 参考文献

1. [工具][https://infoheap.com/online-react-jsx-to-javascript](https://infoheap.com/online-react-jsx-to-javascript)

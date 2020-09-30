1 What are synthetic events in React?
SyntheticEvent is a cross-browser wrapper around the browser’s native event. It’s API is same as the browser’s native event, including
stopPropagation() and preventDefault(), except the events work identically across all browsers.

2What is inline conditional expressions?
You can use either if statements or ternary expressions which are available
from JS to conditionally render expressions. Apart from these approaches,
you can also embed any expressions in JSX by wrapping them in curly
braces and then followed by JS logical operator &&.jsx harmony <h1>Hello!</h1> { messages.length > 0 &&
!isLogin? <h2> You have {messages.length}
unread messages. </h2> : <h2> You
don't have unread messages. </h2> }

3What are “key” props and what is the benefit of using them in
arrays of elements?
A key is a special string attribute you should include when creating arrays
of elements. Keys help React identify which items have changed, are added,
or are removed.
Most often we use IDs from our data as keys:
jsx harmony const todoItems = todos.map((todo) => <li
key={todo.id}> {todo.text} </li> )
When you don’t have stable IDs for rendered items, you may use the item
index as a key as a last resort:
jsx harmony const todoItems = todos.map((todo, index) =>
<li key={index}> {todo.text} </li> )
Note:
1. Using indexes for keys is not recommended if the order of items
may change. This can negatively impact performance and may cause
issues with component state.
2. If you extract list item as separate component then apply keys on list
component instead of li tag.
3. There will be a warning message in the console if the key prop is not
present on list items.
 
4 What is the use of refs?
The ref is used to return a reference to the element. They should be
avoided in most cases, however, they can be useful when you need a direct
access to the DOM element or an instance of a component

5How to create refs?
There are two approaches
1. This is a recently added approach. Refs are created using
React.createRef() method and attached to React elements via the
ref attribute. In order to use refs throughout the component, just
assign the ref to the instance property within constructor.
jsx harmony class MyComponent extends React.Component {
constructor(props) { super(props) this.myRef =
React.createRef() } render() { return <div ref={this.myRef}
/> } }
2. You can also use ref callbacks approach regardless of React version. For example, the search bar component’s input element
accessed as follows, jsx harmony class SearchBar extends
Component { constructor(props) { super(props);
this.txtSearch = null; this.state = { term: '' };
this.setInputSearchRef = e => { this.txtSearch
= e; } } onInputChange(event) { this.setState({
term: this.txtSearch.value }); } render() { return
( <input value={this.state.term}
onChange={this.onInputChange.bind(this)} ref={this.setInputSearchRef}
/> ); } }
You can also use refs in function components using closures. Note: You
can also use inline ref callbacks even though it is not a recommended
approach
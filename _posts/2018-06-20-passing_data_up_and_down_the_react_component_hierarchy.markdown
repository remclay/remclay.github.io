---
layout: post
title:      "Passing data up and down the React component hierarchy"
date:       2018-06-20 00:21:44 -0400
permalink:  passing_data_up_and_down_the_react_component_hierarchy
---


Generally speaking, the fewer components in your React app that maintain state, the better. As such, understanding how to pass data between the components that do maintain state and those that don’t is essential to building an efficient, reliable React app.

React has *“top-down”* data flow (aka “unidirectional” data flow, one-way data flow, one-way binding). Among other things, this improves performance, makes debugging easier, and keeps everything modular. However, we often need data flow in the *“bottom-up”* direction. The flow of data from child to parent in React is explicit. Implementing it requires a few extra lines of code, but is relatively straightforward once you understand how components can pass data to one another.

This post will take a look at passing data both up and down the component hierarchy.

## "Top-down" data flow

Passing data down the hierarchy is fairly straightforward. A parent component can pass it’s state, props, or functions down to its child component as props (properties) when it renders the child component.

### A code snippet is worth a thousand words

Let’s say we’ve built a simple app where users can browse a collection of pets, filtered by animal type. Our container component (parent component) will maintain state and is where we will declare functions responsible for handling changes in the child components. 

It might look something like this:

```
class PetListContainer extends React.Component {
  constructor() {
    super();
    this.state = {
      pets: [],
      filters: [],
      currentFilter: "all"
    }
  }

  componentDidMount() {
    fetch("https://all-the-pets/api/pets")
      .then(response => response.json())
      .then(pets => this.setState({ pets }));
  }

  handleFilterChange = (event) => {
    this.setState({currentFilter: event.target.value});
  }

  render() {
    return (
      <div>
        <FilteredPetList currentFilter={this.state.currentFilter} pets={this.state.pets} />
        <Filter handleFilterChange={this.handleFilterChange} currentFilter={this.state.currentFilter} filters={this.state.filters} />
      </div>
    )
  }
}
```

*import and export lines, rendering PetListContainer to DOM etc omitted

The component fetches some data from an API, and updates the state accordingly. It might have a similar function for fetching the filters. It also responds to user input (the user selecting a filter) and updates state accordingly. It also renders the two child components.

Let’s first look at the `FilteredPetList` component.

### Passing *state* to child components

We said our container component is responsible for updating and maintaining state. As such, for our `PetList `component we can define a stateless functional component.

```
const FilteredPetList = ({ currentFilter, pets }) => {
  const list = currentFilter === 'all' ? pets : pets.filter(pet => pet.type === currentFilter);
  return (
    <ul className="pet-list">
      {list.map((pet) => <li key={pet.id}> {pet.name} - {pet.age} </li>)}
    </ul>
  );
}
```

This component filters the pets array to retrieve the pets whose type match `currentFilter`, and displays that data in an unordered list.

We can see that `FilteredPetList` has access to all props passed in from it’s parent component, simply by wrapping the prop name in curly braces.

## Implementing “bottom-up” data flow
### Passing *functions* to child components

Now let’s look at a component that needs to pass data to it’s parent component. Our `Filter `component can be another stateless functional component but rather than simply displaying data, it will also take in user input. 

```
const Filter = ({ handleFilterChange, currentFilter, filters }) => {
  return (
    <select onChange={handleFilterChange}>
      {filters.map(filter =>
        <option key={filter} value={filter}>{filter}</option>
      )}
    </select>
  );
}
```

This component renders a drop-down list of filters, allowing a user to select one. When a user selects a new filter, we need to reflect that change by updating the state. Components should only update their own state, so we need to tell our `PetListContainer` component about the change. This is what our `handleFilterChange` prop is for.

The `onChange` event in the select tag will fire each time a user selects a new filter. It calls the `handleFilterChange` function, passing in the event as an argument. Recall, this is the function we defined in our `PetListContainer `component, and passed down to our `Filter `component as a prop.

`handleFilterChange` calls `setState`, setting `currentFilter `to the filter selected by the user (accessed via `event.target.value`). State change triggers a re-render of `PetListContainer`, re-rending the child components, passing in the updated props (which reflect the new state).

### Other reasons to "lift" state up

As well as dealing with user input, passing information “back up” the hierarchy is also necessary when you want to share state among children. *“Lifting state up”* is the process of passing data up to the closest common ancestor of the components that need to share it. Upon updating state, a re-render occurs and the updated state is passed down to all applicable child components.

## Recap

To recap, a parent component’s state, props or functions can be passed to child components as props. This eliminates the need for child components to maintain state and allows them to be defined as stateless functional components.

Passing a parent component’s functions as props, and calling those functions on certain events, allows data to be passed back up the hierarchy. The parent container can then update it’s state, and pass down the updated state to any applicable child components.

Hopefully this clears up any confusion about passing data up and down the hierarchy!




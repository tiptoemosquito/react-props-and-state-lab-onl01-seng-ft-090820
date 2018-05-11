# React Props and State Lab

## Overview

You'll build a small React application where you'll update state in response to a JSON payload and pass props among components to handle updates.

## Animal Shelter

![Best Friends](https://media.giphy.com/media/xTiTnz5OOUn49wKbg4/giphy.gif)

Time to put all of our hard-earned knowledge to the test! This lab is fairly big, and will require you to use everything you've learned up
to this point. Don't be intimidated, there are plenty of tests to guide you
along the way! In this lab, we'll be working on a front-end for an animal
shelter. Sadly, there still are way too many cute pets without any owners. Let's
help them out by creating a UI in React!

We **strongly** recommend completing this lab using Behavior Driven Development (BDD)––test the functionality in the browser **before** running the tests. You'll have a much better time seeing the results in the browser.

Call `npm i && npm start` to run this project in your browser

On a high level, you will be working on several components that form the UI of the animal shelter adoption application. Users can filter for pets by type, and can adopt a pet of their choosing. Once a pet is adopted, they cannot un-adopt it. No backsies!

There are several components that need your attention. All of these components can be found in the `components/` folder. Starting from the top and following the data down:

### `App`

1.  The app's initial state is already defined. App has two children: the `<Filters />` and `<PetBrowser />` components.

* `<Filters />` needs a **callback** prop, `onFindPetsClick`. When the `<Filters />` component calls `onFindPetsClick`, `<App />` should fetch a list of pets using `fetch()`.

  * The URL of the API is `/api/pets` with an **optional query parameter**.
  * Use app's `state.filters` to create this parameter
  * If the `type` is `'all'`, send a request to `/api/pets?type=all`
  * If the `type` is `'cat'`, send a request to `/api/pets?type=cat`. Do the same thing for `dog` and `micropig`.
  * Finally, set App's `state.pets` so you can pass this data down as props to `<PetBrowser />`

  * **Even though we're using `fetch` here, its responses have been mocked in order to make the tests work properly. That means it's important to use the _exact_ URLs as described above, or your tests will fail!**

* App should pass a **callback** prop, `onChangeType`, to `<Filters />`. This callback needs to update `<App />`'s `state.filters.type`

### `Filters`

1.  Should have an `onChangeType` callback prop. This callback prop gets called whenever the value of the `<select>` element changes with the **value** of the `<select>`

* Should have an `onFindPetsClick` callback prop. This callback prop gets called when the users clicks the 'Find pets' button.

### `PetBrowser`

1.  Should have a `pets` prop. This is an array of pets that the component uses to render `<Pet />` components. App should determine which pets to pass down as props. App should be responsible for filtering this list based on the types of pets the user wants to see.

* Should have an `onAdoptPet` prop. This callback prop gets passed to its `<Pet />` children components.
* Should have an `adoptedPets` prop. Use this prop to figure out if a pet is adopted or not, and pass that result to the `<Pet />` components in the form of an `isAdopted` prop.

### `Pet`

1.  Should have a `pet` prop. Use the attributes in this data to render the pet card correctly. It should show the pet's `name`, `type`, `age` and `weight`. Based on the pet's `gender`, the component also needs to contain either a male (`♂`) or female (`♀`) symbol.
2.  Should have an `isAdopted` prop. Using this prop, render the correct button in the pet's card; if the pet is adopted, show the disabled button. Otherwise, show the primary button to adopt the pet.
3.  Should have an `onAdoptPet` callback prop. This callback prop gets called with the pet's `id` when the user clicks the adopt pet button — _not_ when they click the disabled button!

## Resources

* [Forms](https://facebook.github.io/react/docs/forms.html)
* [Events](https://facebook.github.io/react/docs/events.html)

<p class='util--hide'>View <a href='https://learn.co/lessons/react-props-and-state-lab'>Props And State Lab</a> on Learn.co and start learning to code for free.</p>

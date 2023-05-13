# car-stock-example

  

## Project setup
```
yarn install
yarn serve
```
# Why I chose vue?
Vue is more flexible compared to other frameworks. I have been using Vue for a long time and I thought that this case would be better created in this way.

# Folder structure

 - **App.vue**: Like other Vue applications, the project starts from here. There are no routes in my project, but general topics such as route handling can be done here
 - **components**: This folder was prepared for shared components such as 'Button' and 'Loader' that will be used throughout the project, as well as for views such as 'AppContainer'.
 - **modules**:  
 - - Modules were created to separate each screen with its own workflow. There are two modules in this project called 'EditPage' and 'EntryPage'.
 - - In each module, a folder was created for the components, mixins, and store operations used (or that could be used) within that module.
 - - This structure aims to help developers easily find what they are looking for in the project and make the necessary development by creating separate modules for each screen with their own workflow, and separate folders for components, mixins, and store operations that can be used in each module.

# Packages

- The project was created with Vue 2. Vue 3 was not preferred because there was no need for the Composition API tools for a complex business requirement.
- Axios package has been included for making HTTP requests.
- The lodash package was included because the "isEqual" method of lodash is needed for the deep comparison of two objects.

# Components
## App.vue
It only calls the AppContainer component. The reason for not performing any operation in this component is that it can be used when something general needs to be added.

## Container.vue
If the project had a more complex structure, state management tools such as Vuex and Pinia could have been used for this operation. However, props were sufficient for this project.

## Button.vue
It was created as a shared component that can be called and used from anywhere in the project. The props used are:
-   "text": For the button label
-   "cancel": To create a red cancel button
-   "disabled": The button state can be disabled in certain situations. This is used for control.

## Loader.vue
This is a loader designed with SCSS. It was created to display a loading circle on the screen when there are situations such as an HTTP request being made on a page in the project.

## EntryPage/index.vue
This component contains a table made up of the "cars" list.
It is used as a wrapper and contains an HTML table. The content of the table is divided into two components: CarListHeader and CarListItem. 	  The CarListItem component uses a v-for loop to iterate over each element in "cars" and passes the "car" object as props.

## EntryPage/components/CarListHeader.vue
It includes the table header and style codes.

## EntryPage/components/CarListItem.vue
This component takes the "car" object as a prop and lists it.
-   It has a computed property for the true/false values of the "inStock" variable.
-   For the "color" column, it displays a circle in the color specified by style binding.

## EditPage/index.vue
An update form screen where the selected "car" object's specified fields can be updated.

-   If no changes have been made, the Save button will be disabled.
-   For the Horse Power input, if a value other than 100 and 550 is entered, a warning message is displayed and the Save button is disabled.
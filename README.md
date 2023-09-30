# Vite Vue Starter

This is a project template using [Vite](https://vitejs.dev/). It requires [Node.js](https://nodejs.org) v12+.

To start:

```sh
npm install
npm run dev

# if using yarn:
yarn
yarn dev
```

## Task
Create a component that is a toggle switch that should be reused. 
It must have the ability to have a "placeholder" / label on both sides of the switch.
It must receive the value it has and send back an update when clicked. In addition, it has a disabled state.
> I read this as the component should be able to be used as a controlled component. Bonus points for also being able to be used as an uncontrolled component (with a default value) to support sending values as a form.

It should have a transition between these unchecked, checked and disabled.
> I'm thinking CSS-transition, but I'll look into Vue's transition component.

Remember to use TypeScript, SCSS, BEM (style), script setup, SFC (vue)


## Thoughts

Without the full context of how the component is to be used, it's easy to go overboard...
I was tipped to not overthink this, so I'll try to keep it simple.

I'm thinking the component should be a wrapper around a native `<input type="checkbox">` element, and then we can style it with CSS.
This to make it accessible and to make it work with forms for good measure.

### Controlled component
When using the component, we should be able to do something like this:
```vue
<ToggleSwitch v-model="value" :disabled="disabled" left-label="Off" right-label="On"/>
```
That would use a two-way binding to `value` and make it a controlled component.

Alternatively support a `@change`-handler:
```vue
  <ToggleSwitch :value="value" :disabled="disabled" left-label="Off" right-label="On" @change="handleChange" />
```
This would functionally be the same as the first example, but could be nice if we want to do something else on change.

### Uncontrolled component
For an uncontrolled component, we could do something like this:
```vue
  <ToggleSwitch :default-value="value" :disabled="disabled" left-label="Off" right-label="On" />
```

### Controlled and uncontrolled component
There is really not any reason why we couldn't do both at the same time. Except for some added complexity.

### On the disabled state...
Didn't mention if the label should have any different styling when disabled.
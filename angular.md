# Angular Notes

## Displaying Data

* Interpolation with double curly braces to display a component property.
* ngFor to display an array of items.
* A TypeScript class to shape the model data for your component and display properties of that model.
* ngIf to conditionally display a chunk of HTML based on a boolean expression.

## Template Syntax

### Template Expressions

JavaScript expressions that have or promote side effects are prohibited, including:

* assignments (=, +=, -=, ...)
* new
* chaining expressions with ; or ,
* increment and decrement operators (++ and --)

Other notable differences from JavaScript syntax include:

* no support for the bitwise operators | and &
* new template expression operators, such as |, ?. and !.

### Expression guidelines

Template expressions can make or break an application. Please follow these guidelines:

* No visible side effects
* Quick execution
* Simplicity
* Idempotence

> ### HTML attribute vs. DOM property
> The distinction between an HTML attribute and a DOM property is crucial to understanding how Angular binding works.
>
> Attributes are defined by HTML. Properties are defined by the DOM (Document Object Model).
> 
> A few HTML attributes have 1:1 mapping to properties. 
> * id is one example. 
> * Some HTML attributes don't have corresponding properties. colspan is one example.
> * Some DOM properties don't have corresponding attributes. textContent is one example.
> * Many HTML attributes appear to map to properties ... but not in the way you might think!
> 
> That last category is confusing until you grasp this general rule:
> 
> Attributes initialize DOM properties and then they are done. Property values can change; attribute values can't.
> 
> For example, when the browser renders `<input type="text" value="Bob">`, it creates a corresponding DOM node with a value property initialized to "Bob".
> 
> When the user enters "Sally" into the input box, the DOM element value property becomes "Sally". But the HTML value attribute remains unchanged as you discover if you ask the input element about that attribute: input.getAttribute('value') returns "Bob".
> 
> The HTML attribute value specifies the initial value; the DOM value property is the current value.
> 
> The disabled attribute is another peculiar example. A button's disabled property is false by default so the button is enabled. When you add the disabled attribute, its presence alone initializes the button's disabled property to true so the button is disabled.
> 
> Adding and removing the disabled attribute disables and enables the button. The value of the attribute is irrelevant, which is why you cannot enable a button by writing `<button disabled="false">Still Disabled</button>`.
> 
> Setting the button's disabled property (say, with an Angular binding) disables or enables the button. The value of the property matters.
> 
> The HTML attribute and the DOM property are not the same thing, even when they have the same name.

* FormsModule is required to use ngModel
* `NgModel` directive only works for an element supported by a `ControlValueAccessor` that adapts an element to this protocol. The `<input>` box is one of those elements. Angular provides value accessors for all of the basic HTML form elements.

### Misc

* The NgForOf directive may perform poorly, especially with large lists. Angular can avoid this churn with trackBy. Add a method to the component that returns the value NgForOf should track. 
> `trackByHeroes(index: number, hero: Hero): number { return hero.id; }`
* Remember that all components are directives.
* All data bound properties must be TypeScript public properties. Angular never binds to a TypeScript private property.
* Use template variables to refer to elements — The newHero template variable refers to the `<input>` element. You can reference newHero from any sibling or child of the `<input>` element.
* Pass values, not elements — Instead of passing the newHero into the component's addHero method, get the input box value and pass that to addHero.
* Keep template statements simple — The (blur) event is bound to two JavaScript statements. The first statement calls addHero. The second statement, newHero.value='', clears the input box after a new hero is added to the list.
* Use ngOnInit() for two main reasons:
    1. To perform complex initializations shortly after construction.
    2. To set up the component after Angular sets the input properties.
* Put cleanup logic in ngOnDestroy(), the logic that must run before Angular destroys the directive.
* Never put content between a component's element tags unless you intend to project that content into the component.

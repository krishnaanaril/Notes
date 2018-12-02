# Angular Notes

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

# Angular Notes

* The NgForOf directive may perform poorly, especially with large lists. Angular can avoid this churn with trackBy. Add a method to the component that returns the value NgForOf should track. 
> `trackByHeroes(index: number, hero: Hero): number { return hero.id; }`
* 
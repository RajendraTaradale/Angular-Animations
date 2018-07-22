# Angular-Animations

Set Up Dependencies

import { BrowserAnimationsModule } from '@angular/platform-browser/animations';

@NgModule({
    imports: [
        BrowserAnimationsModule
  ]
})

#To Support legacy browsers Go to Pollyfill.ts and line no:  or Search below text and uncomment and run npm command

/** IE10 and IE11 requires the following to support `@angular/animation`. */
//import 'web-animations-js';  // Run `npm install --save web-animations-js`.


Angular Animation Methods
Let's talk briefly about the purpose of each of these methods:

trigger(): accepts a name for the animation trigger and an array of state and transition methods to configure the animation</br>
state(): accepts the name of the state of the animation, such as 'active' or 'inactive', and styles that should be applied conditionally when in that state</br>
style(): sets CSS styles and can be passed in to configure a state, transition, or animation</br>
transition(): accepts a string explaining which states are being transitioned and which direction the transition is going (e.g., 'active => inactive'), and any styles or animations to configure the transition</br>
animate(): accepts a numeric duration in milliseconds, or a CSS string specifying both the duration and easing (e.g., 250 or '250ms ease-in')

</br>
State *: element is present </br>
State void: element is removed </br>
Transition void => *: element is being added (alias: :enter) </br>
Transition * => void: element is being removed (alias: :leave) </br>

---Common animation file

import { trigger, transition, style, animate, state } from '@angular/animations';

export const expandCollapse = trigger('expandCollapse', [
  state('*', style({'overflow-y': 'hidden'})),
  state('void', style({'overflow-y': 'hidden'})),
  transition('* => void', [
    style({height: '*'}),
    animate('250ms ease-out', style({height: 0}))
  ]),
  transition('void => *', [
    style({height: 0}),
    animate('250ms ease-in', style({height: '*'}))
  ])
]);

----- Use in component file

import { expandCollapse } from './../../../core/expand-collapse.animation';

@Component({
     animations: [expandCollapse]
})

----Use in Html

 <div class="dtclass" *ngIf="true" [@expandCollapse]>
 
 ---Simple---

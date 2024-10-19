```ts
import { Directive, ElementRef, Input } from '@angular/core';

/**
 * Prevents the screen from scrolling if any children for this element are
 * added or removed.
 */
@Directive({ selector: '[appPreventDomScroll]' })
export class PreventDomScrollDirective {
  @Input('appPreventDomScroll')
  set preventScroll(prevent: boolean) {
    if (prevent) this.lock(this.elementRef.nativeElement);
    else this.unlock();
  }

  private cachedYPosition = 0;
  private mutationObserver = new MutationObserver(() => this.resetScroll());
  private locked = false;
  constructor(private elementRef: ElementRef<HTMLElement>) {}

  private lock(elm: HTMLElement): void {
    if (!this.locked) {
      this.locked = true;

      // Store current window scroll position to revert to if necessary
      this.cachedYPosition = window.scrollY;

      this.mutationObserver.observe(elm, {
        childList: true,
        subtree: true
      });

      console.log('locked');
    }
  }

  private unlock(): void {
    console.log('unlocked');
    this.locked = false;
    this.mutationObserver.disconnect();
  }

  private resetScroll() {
    window.scroll(0, this.cachedYPosition);
    console.log('reset scroll');
  }
}

```

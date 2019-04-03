Add clss to body tag
=============

> link : https://stackoverflow.com/questions/43542373/angular2-add-class-to-body-tag

~~~typescript
import { Component, OnInit, Renderer2 } from '@angular/core';

constructor(private renderer: Renderer2) { }

  // change menu
  toggleMenu() {
    this.navToggleFlag = !this.navToggleFlag;

    if (this.navToggleFlag) {
      this.renderer.addClass(document.body, 'nav-md');
      this.renderer.removeClass(document.body, 'nav-sm');
    } else {
      this.renderer.addClass(document.body, 'nav-sm');
      this.renderer.removeClass(document.body, 'nav-md');
    }
  }

~~~
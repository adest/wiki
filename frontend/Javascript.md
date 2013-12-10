Article
=======
Code structure
--------------
* [AngularJS DI vs requireJS ou comment modulariser du code js](http://solutionoptimist.com/2013/09/30/requirejs-angularjs-dependency-injection/) ++++ 

Angular
-------
* [Create reusable components](http://blog.revolunet.com/blog/2013/11/28/create-resusable-angularjs-input-component/)
* [Follow previous article, but treat about test aspect](http://blog.revolunet.com/blog/2013/12/05/unit-testing-angularjs-directive/)

Manipulation du DOM
===================
* [jQuery](https://jquery.org/)
   * [Onepage scroll](http://www.thepetedesign.com/demos/onepage_scroll_demo.html) Plugin pour faire une navigation a base de scroll basé sur les section html 5

Framework
=========
* [AngularJS](http://angularjs.org/)
   * [Angular chart](http://chinmaymk.github.io/angular-charts/)
* [AngularUI](http://angular-ui.github.io/)

Third party
===========
* Data-Driven Documents
    * Permet de manipuler le DOM en fonction de données. Cas typique d'utilisation des charts en fonction de données, ou un tableau en fonction de ses même données. etc.
    * d3.js [d3js](http://d3js.org/) Framework data driver document

Conflit lib JS
==============

    (function( $ ) {
      $(function() {
        // More code using $ as alias to jQuery
      });
    })(jQuery);

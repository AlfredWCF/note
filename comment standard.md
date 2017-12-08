# Javascript #
use JSDoc annotations

        /**
        * @type {{a: boolean, b: boolean, c: number}}
        */
        var x = {a: true};
        x.b = false;
        x. // <- "x" is shown as having properties a, b, and c of the types specified

        /**
        * @param {string} param1 - The first argument to this function
        */
        function Foo(param1) {
            this.prop = param1; // "param1" (and thus "this.prop") are now of type "string".
        }


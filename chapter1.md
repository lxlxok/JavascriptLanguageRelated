### How to understand module?

> node.js  vs ES6

node.js and common JS use `require`   and  `module.exports=   or   exports=`

ES6 use `import` and `export`

> How to export module under different environment

Herse is a generic code for export module, For commonJS we use `exports`.For require.js we use `define`

Otherwise we bind the object to window or global

    (function () {
        // Establish the root object, `window` in the browser, or `global` on the server.
        var root = this;
        var _ = function (obj) {
                return new wrapper(obj);
            };
        if (typeof exports !== 'undefined') {
            if (typeof module !== 'undefined' && module.exports) {
                exports = module.exports = _;
            }
            exports._ = _;
        } else if (typeof define === 'function' && define.amd) {
            // Register as a named module with AMD.
            define('underscore', function () {
                return _;
            });
        } else {
            root['_'] = _;
        }
    }).call(this);




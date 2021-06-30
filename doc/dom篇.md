# dom篇

1. check if an element is a descendant of another

```
const isDescendant = (child, parent) => parent.contains(child);
```

2. check if an element is focused

```
const hasFocus = ele => (ele === document.activeElement);
```

3. check if the touch events are supported

```
const touchSupported = () => ('ontouchstart' in window || window.DocumentTouch && document instanceof window.DocumentTouch);
```

4. check if user scrolls to the bootom of the page

```
const isAtBottom = () => document.documentElement.clientHeight + window.scrollY >= documentElement.scrollHeight;
```

5. detect internet explorer browser

```
const isIE = !!document.documentMode;
```

6. detect macOS browser

```
const isMacBrowser = /Mac|iPod|iPhone|iPad/.test(navigator.platform);
```

7. get all siblings of an element

```
const siblings = ele => [].slice.call(ele.parentNode.children).filter((child) => (child !== ele));
```

8. get the position of an element relative to the document

```
const getPosition = ele => (r = ele.getBoundingClientRect(), {left: r.left + window.scrollX, top:r.top + window.scrollY})
```

9. get the selected text

```
const getSelectedText = () => window.getSelection().toString();
```

10. go back to the previous page

```
history.back();

//or 
history.go(-1);
```

11. hide an element

```
const hide = ele => ele.style.display = 'none';

//or
const hide = ele => ele.style.visibility = 'hidden';

//or
const hide = ele => ele.hidden = true;
```

12. insert an element after other one

```
const insertAfter = (ele, anotherEle) => anotherEle.parentNode.insertBefore(ele, anotherEle.nextSibling);

//or 
const insertAfter = (ele, anotherEle) => anotherEle.insertAjacentElement('afterend', ele);
```

13. insert an element before other one

```
const insertBefore = (ele, anotherEle) => anotherEle.parentNode.insertBefore(ele, anotherEle);

//or 
const insertBefore = (ele, anotherEle) => anotherEle.insertAdjacentElement('beforebegin', ele);
```

14. insert given html after an element

```
const insertHtmlAfter = (html, ele) => ele.insertAdjacentHTML('afterend', html);
```

15. insert given html before an element

```
const insertHtmlBefore = (html, ele) => ele.insertAdjacentHTML('beforebegin', html);
```

16. redirect to another page

```
const goTo = url => location.href = url;
```

17. reload the current page

```
const reload = () => location.reload();

//or
const reload = () => (location.href = location.href);
```

18. replace an element

```
const replace = (ele, newEle) => ele.parentNode.replaceChild(newEle, ele);
```

19. scroll to top of the page

```
const goToTop = () => window.scrollTo(0,0);
```

20. serialize form data

```
const serialize = formEle => Array.from(new FormData(formEle)).reduce((p,[k, v]) => Object.assign({}, p, {[k]: p[k]?(Array.isArray(p[k]?p[k]:[p[k]]).concat(v):v}),{});
```

21. show an element

```
const show = ele => ele.style.display = '';
```

22. strip html from a given text

```
const stripHtml = html => (new DOMParser().parseFromString(html, 'text/html')).body.textContent || '';
```

23. toggle an element

```
const toggle = ele => (ele.style.display = (ele.style.display === 'none') ? 'block' : 'none');

//or
const toggle = ele => ele.hidden = !ele.hidden;
```

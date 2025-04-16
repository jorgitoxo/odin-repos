## 1. First of all, try giving the search box a consistent width, height, padding, and border color across browsers.

```
    body {
        ...;
        max-width: 400px;
        font-family: "Josefin Sans", sans-serif;
    }

    input {
        width: 100%;
        padding: 5px;
        height: 30px;

        -webkit-appearance: none;
        appearance: none;
        
        border-width: 1px;
        border-color: #666;
        border-style: solid;
        border-radius: 3px;
    }
```

## 2. You'll find that some browsers will not behave in terms of the form element's height. This is due to native OS styling being used in some cases. How can you remove this native styling?
```
    input[type="search"] {
        -webkit-appearance: none;
        appearance: none;
    }

    OR

    input[type="search"] {
        border-color: #666;
    }
```
> See: [Taming search boxes](https://developer.mozilla.org/en-US/docs/Learn_web_development/Extensions/Forms/Advanced_form_styling#taming_search_boxes)

## 3. Once you've removed the native styling, you'll need to add back one of the features it was providing, to keep the same look and feel we originally had. How do you do this?
> Answer: rounded corners!
```
    input {
        ...
        border-radius: 3px;
    }
```

## One thing that is inconsistent across browsers (particularly looking at Safari here) is the position of the standard blue focus outline. How can you remove this?
`outline: none;`

## There is a major problem with just getting rid of the blue focus outline. What is it? Can you add some kind of styling back in so that users can tell when the search box is being hovered or focused?
> **Problem:** hard to determine active/focused state

**Answer:**
```
    <!-- Required for Firefox and Safari -->
    :focus-visible {
    outline: none;
    border-width: 2px;
    border-color: #333;
    border-style: solid;
    border-radius: 3px;
    }

    input:hover, input:focus {
        background-color: #e7e7e7;
    }
```

## Another thing that commonly denotes a search box is a magnifying glass icon. We've made one available in the same directory as our HTML files — see search-24px.png — plus a <div> element after the search input to help you attach it, should you need it. Can you figure out a sensible way to attach it, and can you use some CSS to get it to sit to the right of the search box, and be lined up vertically as well?
```
<!-- My solution -->
form {
    display: flex;
}

form > div {
    position: relative;
}

form > div::after {
    position: absolute;
    top: 5px;
    left: 5px;
    width: 24px;
    height: 24px;
    content: "";
    background: #fff url(../search-24px.png) no-repeat;
}
```

```
<!-- MDN solution -->
form {
    display: flex;
    align-items: center;
}

div {
    width: 36px;
    height: 24px;
    background: url(../search-24px.png) no-repeat center;
    background-size: 18px;
}
```

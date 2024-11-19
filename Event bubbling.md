<h1>What is Event Bubbling in JavaScript?</h1>

In **Event bubbling**, when an event (like a click) occurs on an element, it first triggers the event handler on that element, then propagates upward to its ancestors, all the way to the document root.

This process allows **child elements** to "bubble up" their events to their **parent elements**.

----

**Event Bubbling in Action**

To observe bubbling, let's log the order of events when clicking the button:

```ruby
<div id="grandparent">
  <div id="parent">
    <button id="child">Click Me</button>
  </div>
</div>

<script>
  document.getElementById('grandparent').addEventListener('click', () => {
    console.log('Grandparent clicked');
  });

  document.getElementById('parent').addEventListener('click', () => {
    console.log('Parent clicked');
  });

  document.getElementById('child').addEventListener('click', () => {
    console.log('Child clicked');
  });
</script>
```

**What Happens If You Click the Button?**

1.  **Button's Listener Executes**: Logs "Child clicked".

2.  **Parent's Listener Executes**: Logs "Parent clicked".

3.  **Grandparent's Listener Executes**: Logs "Grandparent clicked".


----


**Stopping Event Bubbling**

Sometimes, you may not want an event to bubble up to its ancestors. You can stop it using the stopPropagation() method.

```ruby
<div id="parent">
  <button id="child">Click Me</button>
</div>

<script>
  document.getElementById('parent').addEventListener('click', () => {
    console.log('Parent clicked');
  });

  document.getElementById('child').addEventListener('click', (event) => {
    console.log('Child clicked');
    event.stopPropagation(); // Stops the event here
  });
</script>
```
**What Happens If You Click the Button?**

-  Logs "Child clicked".

-  The parent's listener will **not** execute because bubbling is stopped.

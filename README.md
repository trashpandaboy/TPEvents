# TPEvents

TPEvents is a simple event system for Unity, designed to facilitate event management within your Unity projects.

## Installation

To install TPEvents, please use the UnityPackageManager

## Usage

### Adding a Listener

To add a listener to an event, use the `StartListening` method:

```csharp
EventDispatcher.StartListening("eventName", listeningAction);
```

### Removing a Listener

To remove a listener from an event, use the [`StopListening`](command:_github.copilot.openSymbolFromReferences?%5B%22StopListening%22%2C%5B%7B%22uri%22%3A%7B%22%24mid%22%3A1%2C%22fsPath%22%3A%22%2FUsers%2Fwilliamsoro%2FSource%2FTPEvents%2FEventDispatcher.cs%22%2C%22external%22%3A%22file%3A%2F%2F%2FUsers%2Fwilliamsoro%2FSource%2FTPEvents%2FEventDispatcher.cs%22%2C%22path%22%3A%22%2FUsers%2Fwilliamsoro%2FSource%2FTPEvents%2FEventDispatcher.cs%22%2C%22scheme%22%3A%22file%22%7D%2C%22pos%22%3A%7B%22line%22%3A58%2C%22character%22%3A27%7D%7D%5D%5D "Go to definition") method:

```csharp
EventDispatcher.StopListening("eventName", listeningAction);
```

### Triggering an Event

To trigger an event, use the `TriggerEvent` method:

```csharp
EventDispatcher.TriggerEvent("eventName", eventObject);
```

## Example

Here is a complete example of how to use TPEvents:

```csharp
using UnityEngine;
using UnityEngine.Events;

public class Example : MonoBehaviour
{
    private void OnEnable()
    {
        EventDispatcher.StartListening("TestEvent", OnTestEvent);
    }

    private void OnDisable()
    {
        EventDispatcher.StopListening("TestEvent", OnTestEvent);
    }

    private void OnTestEvent(Object obj)
    {
        Debug.Log("Event received: " + obj);
    }

    private void Update()
    {
        if (Input.GetKeyDown(KeyCode.Space))
        {
            EventDispatcher.TriggerEvent("TestEvent", this);
        }
    }
}
```

## License

This project is licensed under the Unlicense. For more details, see the `LICENSE` file.
Memento Design Pattern: Undo Your Way to Success
The Memento design pattern is a behavioral pattern that allows you to capture and restore the internal state of an object without exposing its implementation. Think of it like a time machine for your objects, letting you rewind to previous states without sacrificing encapsulation.

When to Use Memento
Undo/Redo functionality: Want to enable users to undo or redo changes they make? Memento is your solution.
Reverting to a previous state: Need to restore an object to a known state, like when recovering from an error or switching between configurations? Memento comes in handy.
Version control: If you need to manage different versions of an object or snapshot its state, Memento can help.
Understanding the Memento Pattern Components
Originator: The object whose internal state needs to be saved and restored. It creates a Memento object and stores it.
Memento: A separate object holding a snapshot of the Originator's state. It should be immutable and provide methods to retrieve state information.
Caretaker: An object responsible for storing and retrieving Memento objects. This allows you to keep track of different state snapshots and access them later.
Let's Code!
public class MementoDesignExample {

    public static void main(String[] args) {
        // Create an Editor object (Originator)
        Editor editor = new Editor();
        editor.setText("Initial text");
        System.out.println("Editor text: " + editor.getText());

        // Create a Caretaker to manage Mementos
        Caretaker caretaker = new Caretaker();

        // Create a Memento and store it with the Caretaker
        Memento memento = editor.createMemento();
        caretaker.saveMemento(memento);

        // Modify the Editor's state
        editor.setText("Modified text");
        System.out.println("Editor text: " + editor.getText());

        // Restore to the previous state using the Memento
        editor.restoreMemento(caretaker.retrieveMemento());
        System.out.println("Editor text: " + editor.getText());
    }
}

class Editor {
    private String text;

    public String getText() {
        return text;
    }

    public void setText(String text) {
        this.text = text;
    }

    // Creates a Memento containing the current state
    public Memento createMemento() {
        return new Memento(text);
    }

    // Restores the state from a given Memento
    public void restoreMemento(Memento memento) {
        this.text = memento.getSavedText();
    }
}

class Memento {
    private String savedText;

    public Memento(String savedText) {
        this.savedText = savedText;
    }

    public String getSavedText() {
        return savedText;
    }
}

class Caretaker {
    private Memento memento;

    public void saveMemento(Memento memento) {
        this.memento = memento;
    }

    public Memento retrieveMemento() {
        return memento;
    }
}
Explanation:

The Editor class acts as the Originator. It stores the current text and offers methods to save (createMemento) and restore (restoreMemento) states.
Memento acts as a simple data holder, storing the text as it was when the Memento was created.
Caretaker keeps track of Mementos and provides a way to access them for restoration.
Running the Code:

When you execute this code, you'll see the output illustrating the memento's functionality:
Editor text: Initial text
Editor text: Modified text
Editor text: Initial text
Notice how the "Modified text" is reverted back to "Initial text" after restoring from the memento.
Memento: The Undo/Redo King
The Memento pattern allows you to create powerful Undo/Redo functionalities, adding a crucial feature for users working with text editors, image editing software, and any application that needs state reversibility.

Advantages:

Encapsulation: Memento protects the internal state of the Originator by offering access through well-defined methods.
Flexibility: Memento allows you to have different states stored without exposing Originator's internal implementation.
Maintainability: It promotes cleaner and easier-to-manage code.
By leveraging the Memento design pattern, you can take your application's state management to the next level, providing your users with powerful undo/redo functionality and enhancing their overall experience.

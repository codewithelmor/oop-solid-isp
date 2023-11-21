# Interface Segregation Principle (ISP)

The **`Interface Segregation Principle (ISP)`** states that clients should not be forced to depend on interfaces they do not use. In other words, it's better to have several smaller, specific interfaces than one large, monolithic interface. This principle helps prevent classes from being forced to implement methods they don't need.

Let's illustrate the ISP with a C# example involving a printing interface:

Suppose you have a requirement for a printing system that supports two types of documents: regular documents and photos. You might initially design an interface like this:

```csharp
// A single interface for both regular documents and photos
public interface IPrinter
{
    void PrintDocument();
    void PrintPhoto();
}
```

In this design, any class that wants to implement printing support must implement both the **`PrintDocument()`** and **`PrintPhoto()`** methods, even if it's only interested in one of them.

Now, let's apply the Interface Segregation Principle by splitting this monolithic interface into smaller, more focused interfaces:

```csharp
// Interface for printing regular documents
public interface IDocumentPrinter
{
    void PrintDocument();
}

// Interface for printing photos
public interface IPhotoPrinter
{
    void PrintPhoto();
}
```

With these smaller interfaces, classes can now choose to implement only the interfaces that are relevant to their needs. Here's how you can implement them:

```csharp
public class SimpleDocumentPrinter : IDocumentPrinter
{
    public void PrintDocument()
    {
        Console.WriteLine("Printing a document...");
    }
}

public class AdvancedPhotoPrinter : IPhotoPrinter
{
    public void PrintPhoto()
    {
        Console.WriteLine("Printing a photo...");
    }
}
```

Now, classes can implement the specific interfaces they need without being forced to implement unnecessary methods. This adheres to the Interface Segregation Principle and makes the codebase more maintainable and less prone to errors.

Here's how you can use these classes:

```csharp
class Program
{
    static void Main(string[] args)
    {
        IDocumentPrinter documentPrinter = new SimpleDocumentPrinter();
        IPhotoPrinter photoPrinter = new AdvancedPhotoPrinter();

        documentPrinter.PrintDocument(); // Outputs: Printing a document...
        photoPrinter.PrintPhoto();       // Outputs: Printing a photo...
    }
}
```

In this example, you create instances of classes that implement the specific interfaces they need, demonstrating how the ISP leads to more flexible and focused interfaces.

# Code Snippets for Increased Productivity
This extension houses a collection of useful snippets. To request a new snippet raise an issue or become a contributer!

## Async Xunit Testing
Add a xunit test by typing any of these prefixes
`"prefix": ["new-xunit", "xunit-test"]` and you will see the following code block with tabstops to each area of the signature.
```csharp
namespace MyTestNamespace
{
    using Xunit;
    using Moq;
    public class MyTestClass
    {
        public WhatYouAreTesting_WhatYouAreDoing_WhatYouExpectToHappen()
        {
            // Arrange
            
            // Act
            
            // Assert
            
        }
    }
}
```
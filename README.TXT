Within Visual Studio 2013 using the wizards I have created a bare .NET 4.5 WPF C# application 
which also has a C++/CLI class library. 

When I run the application on my Windows 8 (or Windows 10) development machine 
the app runs just fine. 

However when I run it on a clean Windows 7 machine it crashes 
the moment the C# tries to instantiate an object defined in the C++/CLI class library. 

I have not changed anything in the options, I have just used the wizards to create a C# WPF app and 
a C++ CLR class library, and I have created a ref class in the library, 
and I tried to instantiate the ref class from a button click handler in the WPF window from the C# app.
 
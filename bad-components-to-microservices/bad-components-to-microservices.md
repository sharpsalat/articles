In my .NET Software Development Engineer experience, I've seen many projects struggle with **"bad"** dependencies, packages, libraries, and modules, collectively referred to as 'components' in this article.
That makes it difficult to update the application to a modern version of the language and framework. 
This can result in inability to refactor the application or follow new requirements or replace the components with a another solutions.
In this article, I will discuss how to deal with legacy dependencies in your backend application and provide I believe the best solution for it.

Examples of "Bad" components
-------------------------------

There are several examples of **"bad"** components that can cause problems in your backend application:

1. **Legacy .NET framework packages in .NET Core apps**:  
If you have a .NET Core application, 
but it still depends on legacy .NET Framework packages, 
it can make it difficult to update the application to a modern version of the runtime, language, framework and even other packages.
2. **Memory-unsafe code or libraries**:  
If your application has memory-unsafe code or libraries, 
it can lead to stability issues, security vulnerabilities and make whole app hard to test.
3. **Platform-dependent or environment-dependent components in code**:  
If your application depends on platform-dependent components, 
such as Windows-only components, it can make it difficult to run the application on other platforms.
4. **Security-vulnerable or untrusted components that require isolation**:  
If your application has security-vulnerable components that hard to replace or require isolation, it can lead to stability issues and security vulnerabilities.
5. **Deprecated or outdated packages in the project**:  
If your project uses deprecated or outdated packages, 
it can make it difficult to maintain and update the application over time.
6. **Inconsistent package versions across projects**:  
If different projects use different versions of the same package, 
it can lead to compatibility issues and make it difficult to manage dependencies.
7. **Lack of documentation or support for packages**:  
If a package is no longer maintained or has poor documentation, 
it can make it difficult to troubleshoot issues and get help when needed.
8. **Components are not open source or have unclear licensing terms**:  
Components that are not open source or have unclear licensing terms can make it difficult for you to understand how the component is being used and distributed, which could lead to legal issues if you violate the terms of the license.  
Components with unclear licensing terms may also be proprietary, meaning that they are not available under an open source license and cannot be freely modified or redistributed.

Solution: Move **"Bad"** components into a Separate Microservice
--------------------------------------------------------------

The solution to deal with legacy components is to move them into a separate microservice. This will allow you to keep your application up to date while still maintaining the legacy dependency. Here are some requirements for moving a legacy dependency into a separate microservice.

Requirements
-------------
1. **Ideally, the dependency should be loosely coupled**:   
If you follow the dependency inversion pattern, then moving the legacy dependency or package into a separate microservice can be painless.
2. **In a more complex situation, you will first have to refactor to move the dependency into a separate service**:   
Before replacing the code with the API of the newly developed microservice, you may need to refactor your application to make it following Dependecy injection (DI) pattern that make it easier to replace the legacy dependency.
3. **If the component is tightly coupled with the application's infrastructure**   
It can be difficult to move it into a separate microservice without causing cascading changes throughout the application.  
If the component has complex configuration or deployment requirements that are not easily managed in a separate microservice, 
it may not be possible or worthless to move it into a separate microservice.

Actions
-------

1. Identify the current state of the app:
	* Assess the current state of the application, including its architecture, dependencies, and overall structure.
	* Identify any areas that may be causing issues or hindering progress.
2. Find all necessary "bad" components:
	* Analyze the codebase to identify any components that are causing problems or hindering progress.
    * Sometimes it may be necessary to divide it to multiple microservices
3. Decide whether this solution will work for you:
	* Evaluate whether the identified "bad" components can be addressed with the proposed solution.
	* Consider any potential drawbacks or limitations of the solution before deciding whether to proceed.
4. Create a step-by-step plan:
	* Develop a detailed plan outlining how you will implement the solution, including any necessary changes to the codebase and infrastructure.
	* Ensure that the plan is realistic and achievable within the given timeframe.
    * Don't forget about documenting new microservice and it's API
5. Implement unit and integration tests:
	* Write necessary unit and integration tests on each implementation steps for the new solution to ensure that it functions as expected and does not introduce any regressions.
	* Tests should cover all possible scenarios and edge cases to ensure that the solution is robust and reliable.

Benefits
---------
1. A separate team can work on maintaining old components independently, making development process more flexible.
2. You can start working on new solutions and replace "bad" components smoothly without interrupting main application.
3. Improved performance: By removing or replacing "bad" components, you can improve the overall performance of your application, by simply use newer solutions.
4. Increased maintainability: By simplifying the codebase and reducing complexity, you can make it easier for developers to understand and maintain the application, leading to fewer bugs and errors.

Conclusion
----------

In conclusion, moving "bad" components into a separate microservice is a viable solution for dealing with it in your backend application. This approach allows you to keep your application up to date while still maintaining such components. However, it's important to carefully evaluate whether this solution will work for you and consider any potential drawbacks or limitations before proceeding. And for my point of view, this is one of the justified applications of microservices.
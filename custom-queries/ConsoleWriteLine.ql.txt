import csharp


  @name Console.WriteLine usage
  @description Detects calls to Console.WriteLine, often debug code left in production.
  @kind problem
  @problem.severity warning
  @tags maintainability readability
 

from MethodAccess ma
where ma.getTarget().getDeclaringType().hasQualifiedName(System, Console)
  and ma.getTarget().getName() = WriteLine
select ma, Avoid using Console.WriteLine in production code.

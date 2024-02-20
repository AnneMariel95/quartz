How did I end up being productive and unproductive at the same time?  
  
Day 17 of #100DaysOfCode. #Finance Manager App Update:  
  
From a user perspective:  
If a user wants to delete a category (Food) and Food is a pre defined Category in the database, Food will be deleted  
  
but  
  
From a developer perspective:  
it will actually not be deleted in the database. What backend would do is just delete the Space Category Mapping.  
  
I spent a couple of hours trying to implement the Delete Category Functionality. I encountered a lot of issues before figuring out that a simple @Transactional annotation needs to be added to the repository to delete something that needs multiple operations.  
  

```java
@Transactional  
void deleteByCategoryIdAndSpaceId(String categoryId, String spaceId);}  
```

*pats myself on the back*
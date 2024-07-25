[![official JetBrains project](https://jb.gg/badges/official.svg)](https://confluence.jetbrains.com/display/ALL/JetBrains+on+GitHub)
[![GitHub license](https://img.shields.io/badge/license-Apache%20License%202.0-blue.svg?style=flat)](https://www.apache.org/licenses/LICENSE-2.0)

# Introduction to Coroutines and Channels Hands-On Lab

This repository is the code corresponding to the
[Introduction to Coroutines and Channels](https://play.kotlinlang.org/hands-on/Introduction%20to%20Coroutines%20and%20Channels/01_Introduction)
Hands-On Lab. 

1.Clone project: git clone https://github.com/kotlin-hands-on/intro-coroutines
2.Create GitHub token
3.run src/contributors/main.kt
4.Blocking Request

  .retrofit library https://square.github.io/retrofit/
  .Retrofit turns your HTTP API into a Java interface.

public interface GitHubService {
@GET("users/{user}/repos")
Call<List<Repo>> listRepos(@Path("user") String user);
}

open src/tasks/Request1Blocking.kt
open src/contributors/Contributors.kt

Task 1
The first task helps you familiarize yourself with the task domain. Currently, each contributor's name is repeated several times, once for every project they have
taken part in. Implement the aggregate() function combining the users so that each contributor is added only once. The User Contributions property should contain
the total number of contributions of the given user to all the projects. The resulting list should be sorted in descending order according to the number of
contributions.

Open src/tasks/Aggregation.kt and implement the List<User>.aggregate() function. Users should be sorted by the total number of their contributions.

5.CallBacks
Open src/tasks/Request2Background.kt

fun loadContributorsBackground(
service: GitHubService, req: RequestData,
updateResults: (List<User>) -> Unit
)

loadContributorsBackground(service, req) { users ->
SwingUtilities.invokeLater {
updateResults(users, startTime)
}
}

Task 2
Fix the loadContributorsBackground() function in src/tasks/Request2Background.kt so that the resulting list is shown in the UI.

updateResults(loadContributorsBlocking(service, req))



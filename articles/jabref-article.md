### What is JabRef?
From JabRef official website:
>JabRef is an open-sourced, cross-platform citation and reference management software. It uses BibTeX and BibLaTeX as its native formats and is therefore typically used for LaTeX.

Now let's get to the question, for this one I really enjoyed getting in depth of the question, so if you only want the high level abstraction go to the end for the TLDR.

### How does JabRef creates new articles?
JabRef implements a GUI made with JavaFX, so naturally it implements a java class called JabRefFrame.java that represents the main  interface which the user interacts with.

Here the creation of an article can be triggered by a key binding, there is a lambda that is listening for when you press a key. And then a switch statement catches if the combination of keys triggers a specific behavior on the window.

In this case what we’re interested in the creation of a new article.

When the case of creating a new article is triggered the following happens:
```java
case NEW_ARTICLE:
   new NewEntryAction(this, StandardEntryType.Article, dialogService, prefs, stateManager).execute();
   break;
```
As we can appreciate, a new object called  `NewEntryAction`, this is object has the main logic to register data in JabRef.

In the previous block of code JabRef also executes the `execute` method from `NewEntryAction`.
And there is a key part in the method, which is this:
```java
if (type.isPresent()) {
   jabRefFrame.getCurrentLibraryTab().insertEntry(new BibEntry(type.get()));
}
```
Basically if an entry type is present (in this case is an article) it creates an object called BibEntry with the parameter `Article`

This is how the constructor of `BibEntry` looks like:
```java
public BibEntry(EntryType type) {
   this.id = IdGenerator.next();
   setType(type);
   this.sharedBibEntryData = new SharedBibEntryData();
}
```
Side note:
> An entry can be either added to a `SharedBibEntryData` that is a relational database or a 'normal' entry that would be a file of `BIBTEX_DB` extension that meets with the criteria of LaTex.

When the BibEntry instance is created it becomes part of a list of entries that are contained in an class called `StateManager`. it looks like this:
```java
private final ObservableList<BibEntry> selectedEntries = FXCollections.observableArrayList();
```

Finally we go back to where we started. To the `JabRefFrame.java` file. Here a very important object is instantiated when we try to exit the program.
```java
SaveDatabaseAction saveAction = new SaveDatabaseAction(libraryTab, Globals.prefs, Globals.entryTypesManager);
if (saveAction.save()) {
    return true;
}
```
The object is `SaveDataBaseAction` which takes care of all file writing and database insertion. We have to pay special attention to the third parameter `Globals.entryTypesManager`. Which is a global object that belongs to the class `BibDatabaseContext`that has access to the list of BibEntries that I mentioned.


### TLDR
1.  GUI catches combination of keys to create Article
2.  A new Entry of type `Article` is created
3.  The entry is added to an ArrayList.
4.  When the user tries to exit the GUI an option to save is presented.
5.  If the user agrees, the list of pending entries are saved on the correspondent location

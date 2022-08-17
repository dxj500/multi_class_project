  {{PROBLEM}} Multi-Class Planned Design Recipe

1. Describe the Problem
    As a user
    So that I can record my experiences
    I want to keep a regular diary

    As a user
    So that I can reflect on my experiences
    I want to read my past diary entries

    As a user
    So that I can reflect on my experiences in my busy day
    I want to select diary entries to read based on how much time I have and my reading speed

    As a user
    So that I can keep track of my tasks
    I want to keep a todo list along with my diary

    As a user
    So that I can keep track of my contacts
    I want to see a list of all of the mobile phone numbers in all my diary entries

2. Design the Class System
Consider diagramming out the classes and their relationships. Take care to focus on the details you see as important, not everything. The diagram below uses asciiflow.com but you could also use excalidraw.com, draw.io, or miro.com



            ┌─────────────────────┐            ┌─────────────────────┐
            │ Diary               │            │   DiaryEntry        │
            │                     │            │                     │
            │ Add diary entry     │            │   Title             │
            │ List all diary entries           │   Content           │
            │                    ◄┌────────────┼── Count_words       │
            │                     │            │                     │
            │ Reading Time        │            │                     │
            │           ▲         │            │         ▲           │
            └───────────┬─────────┘            │         │           │
                        │                      └─────────┼───────────┘
                        │                                │
            ┌───────────┼──────────┐            ┌────────┼────────────┐
            │           │          │            │        │            │
            │  TodoList │          │            │  Phone Numbers      │
            │                      │            │  Add to list        │
            │  Add to list         │            │  List all           │
            │                      │            │                     │
            │  View List           │            │                     │
            │                      │            │                     │
            │                      │            │                     │
            │                      │            │                     │
            └──────────────────────┘            └─────────────────────┘

class Diary
  def initialize
  list = []
  end

  def add(diary_entry)
  end

  def list_entries
  end

  def reading_time(count_words, wpm, time)
  end

end

class DiaryEntry
  def initialize(title, content)
    ...
  end

  def title
  end

  def contents
  end

  def count_words
  end
end 

class TodoList
  def initialize(task)
    list = []
  end 

  def add_task
  end

  def view_tasks
  end
end

class PhoneNumbers
  def initialize
  list = []
  end

  def add_phone_number
  end

  def view_phone_number
  end
end



Also design the interface of each class in more detail.

3. Create Examples as Integration Tests
Create examples of the classes being used together in different situations and combinations that reflect the ways in which the system will be used.

# EXAMPLE

# Gets all tracks
library = MusicLibrary.new
track_1 = Track.new("Carte Blanche", "Veracocha")
track_2 = Track.new("Synaesthesia", "The Thrillseekers")
library.add(track_1)
library.add(track_2)
library.all # => [track_1, track_2]

4. Create Examples as Unit Tests
Create examples, where appropriate, of the behaviour of each relevant class at a more granular level of detail.

# EXAMPLE

# Constructs a track
track = Track.new("Carte Blanche", "Veracocha")
track.title # => "Carte Blanche"
Encode each example as a test. You can add to the above list as you go.

5. Implement the Behaviour
After each test you write, follow the test-driving process of red, green, refactor to implement the behaviour.
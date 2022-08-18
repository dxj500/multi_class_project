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
            │ Add diary entry     │            │                     │
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

  def time_to_read_content(count_words, wpm)
  end

  def reading_time(spare_time)
  end

end

class DiaryEntry
  def initialize(content)
    ...
  end


  def contents
   #return contents
  end

  def count_words(contents)
    #return number
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

  def add_phone_number(content list)
    get content list from diary entry
    search for phone number
    extract phone number
    add to phone number list
  end

  def view_phone_number
  end
end



Also design the interface of each class in more detail.

3. Create Examples as Integration Tests
Create examples of the classes being used together in different situations and combinations that reflect the ways in which the system will be used.


#1 (add diary entry)
  entry = Diary.new
  diary_entry = DiaryEntry.new(content)
  entry.add(diary_entry)
  entry.list_entries # => [content]

#2 (get time_to_read_content)
  entry = Diary.new
  diary_entry = DiaryEntry.new(content)
  word_count = diary_entry.count_words
  time_to_read_content # => num

#3 (add phone number)
  diary_entry = DiaryEntry.new(content)
  new_number = PhoneNumbers.new
  diary_entry.contents
  diary_entry.add_phone_number 
  new_number.view_phone_number => list of phone numbers



4. Create Examples as Unit Tests
Create examples, where appropriate, of the behaviour of each relevant class at a more granular level of detail.


class Diary
-----------

#construct
diary = Diary.new
diary.list entries => []

diary = Diary.new
diary.reading_time(time) => []

class DiaryEntry
----------------

#construct
entry = DiaryEntry.new
entry.contents => []

entry = DiaryEntry.new(contents)
entry.count_words => number


class TodoList
--------------

# 3 units tests required for this class
#construct



# EXAMPLE

# Constructs a track
track = Track.new("Carte Blanche", "Veracocha")
track.title # => "Carte Blanche"
Encode each example as a test. You can add to the above list as you go.

5. Implement the Behaviour
After each test you write, follow the test-driving process of red, green, refactor to implement the behaviour.
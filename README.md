# Emacs settings

I define this agenda custom commands:

```
 '(org-agenda-custom-commands
   (quote
    (("d" "Daily"
      ((tags "WEEKLY_GOAL" nil)
       (todo "NEXT|IN_PROGRESS" nil)
       (agenda "" nil))
      nil)
     ("rd" "Daily review"
      ((todo "IN" nil)
       (todo "NEXT" nil)
       (todo "TODO" nil)
       (agenda "" nil))
      nil nil)
     ("g" "Goals" tags "GOAL-TODO=\"GOAL\"" nil))))
```

And this capture mode templates (defined inside `templates` folder):

```
 '(org-capture-templates
   (quote
    (("t" "Task" entry
      (file "backlog.org")
      (file "templates/tpl-todo.txt")
      nil nil)
     ("e" "Event" entry
      (file "calendar.org")
      (file "templates/tpl-event.txt"))
     ("s" "Someday" entry
      (file "someday.org")
      (file "templates/tpl-someday.txt"))
     ("i" "Unclassified element (IN)" entry
      (file "backlog.org")
      (file "templates/tpl-in.txt")
      :prepend t :empty-lines-before 1)
     ("g" "Goals")
     ("ge" "Epic Goals" entry
      (file+headline "backlog.org" "Epic Goals")
      (file "templates/tpl-goal.txt")
      :jump-to-captured t :empty-lines-before 1 :empty-lines-after 1)
     ("gl" "Long Goals (2-5 years from now)" entry
      (file+headline "backlog.org" "Long Goals (2-5 years from now)")
      (file "templates/tpl-goal.txt")
      :jump-to-captured t :empty-lines-before 1 :empty-lines-after 1)
     ("gm" "Medium Goals (6 months up to 2 years)" entry
      (file+headline "backlog.org" "Medium Goals (6 months up to 2 years)")
      (file "templates/tpl-goal.txt")
      :jump-to-captured t :empty-lines-before 1 :empty-lines-after 1)
     ("gs" "Short Goals (next 6 months)" entry
      (file+headline "backlog.org" "Short Goals (next 6 months)")
      (file "templates/tpl-goal.txt")
      :jump-to-captured t :empty-lines-before 1 :empty-lines-after 1)
     ("h" "Habit" entry
      (file "calendar.org")
      (file "templates/tpl-habit.txt")))))
```

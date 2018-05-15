# Settings

## Agenda custom commands

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

## Capture templates

(defined inside `templates` folder)

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

## Misc

```

(setq
 org-agenda-start-on-weekday nil
 org-agenda-span 7)

(setq
 org-log-into-drawer "LOGBOOK"
 org-refile-targets (quote ((org-agenda-files :level . 1)))
 org-refile-use-outline-path  (quote file)
 org-refile-allow-creating-parent-nodes (quote confirm))

(setq org-agenda-repeating-timestamp-show-all nil)

(defun org-agenda-toggle-custom-habits ()
  "Toggle display of custom habits in an agenda buffer."
  (interactive)
  (org-agenda-check-type t 'agenda)
  (setq org-custom-habit-show-habits (not org-custom-habit-show-habits))
  (if org-custom-habit-show-habits
      (org-agenda-filter-by-tag "-HABIT" ?\s)
    (org-agenda-filter-show-all-tag))
  (org-agenda-redo))

(org-defkey org-agenda-mode-map "H" 'org-agenda-toggle-custom-habits)
```

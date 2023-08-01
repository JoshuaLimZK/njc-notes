---
creation-date: <% tp.file.creation_date() %>
modification date: <% tp.file.last_modified_date("dddd Do MMMM YYYY HH:mm:ss") %>
tag: dailynotes
banner: "https://images.unsplash.com/photo-1524820197278-540916411e20?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2990&q=80"
banner_y: 0.92771
---
# <% moment(tp.file.title,'YYYY-MM-DD').format("dddd, DD MMMM YYYY") %>

## ⚠️ Tasks
>[!failure]+ Overdue
>```tasks
>not done
>due before <% tp.file.title %>
>short mode
>```

>[!warning]+ Due Soon
>```tasks
>not done
>due  <% tp.file.title %>  <% moment(tp.file.title, "YYYY-MM-DD").add(7, "days").format("YYYY-MM-DD") %>
>short mode
>```

>[!success]- Completed
>```tasks
>done
>short mode
>due  <% tp.file.title %>
>```

## 🏆 Goals for Today
- 

## 👍 What I did Today
- 

## 🤔 Random Thoughts & Notes Dump
- <% tp.file.cursor() %>

## ☑️ New Tasks Today


## 📝 Files Created Today
> [!abstract]- Created Today
>```dataview
>TABLE file.ctime AS "Created on"
>WHERE file.cday = this.file.day   
>SORT file.name asc
>```

## 📝 Files Modified Today
> [!NOTE]- Modified Today
>```dataview
>TABLE file.mtime AS "Last Modified"
>WHERE file.mday = this.file.day   
>SORT file.name asc
>```
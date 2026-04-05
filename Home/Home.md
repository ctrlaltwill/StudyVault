---
title: Home
type: MOC
created: 2026-04-04T14:04
updated: 2026-04-06T07:51
---

> [!welcome] Welcome
> This vault is a demo of a personal StudyVault. It uses a modified PARA method, you can read more about it: [here](https://www.reddit.com/r/ObsidianMD/comments/1sct0nb/obsidian_medical_school/).

> [!multi-column]
>
>> [!resources] Looking for something to read?
>> ```dataviewjs
>> // Get all notes under Areas/ that are NOT folder notes
>> const pages = dv.pages('"Areas"')
>>   .where(p => {
>>     // Exclude the folder note itself (where name equals parent folder name)
>>     const parentFolder = p.file.folder.split('/').pop();
>>     return p.file.name !== parentFolder;
>>   });
>> 
>> let randomNote = null;
>> if (pages.length > 0) {
>>   randomNote = pages[Math.floor(Math.random() * pages.length)];
>>   dv.el('span', `Review your note on [[${randomNote.file.name}]].`, { cls: "random-suggestion", markdown: true });
>> } else {
>>   dv.span("No notes found in Areas.");
>> }
>> ```
>> *This is auto-populated from [[Areas]].*
>
>> [!projects] Looking for something to do?
>> ```dataviewjs
>> const page = dv.page("System/Planning/List of Notes");
>> let suggestion = "a new disorder";
>> if (page) {
>>   const content = await dv.io.load(page.file.path);
>>   const lines = content.split("\n");
>>   const items = [];
>>   for (const line of lines) {
>>     const match = line.match(/^\s*(\d+\.\s+|-\s+)(.+)$/);
>>     if (match) items.push(match[2].trim());
>>   }
>>   if (items.length) suggestion = items[Math.floor(Math.random() * items.length)];
>> }
>> dv.el('span', `Create a note on [[${suggestion}]].`, { cls: "random-suggestion", markdown: true });
>> ```
>> *You can edit these in [[List of Notes]] (remove when created).*

# Table of Contents
1. **[[Areas]]** – summarised knowledge by domain.
2.  **[[Projects]]** – time-focused study and work projects. 
3.  **[[Resources]]** – reference materials that connects areas and project knowledge.
4. **[[System]]** – vault backend: attachments and templates. 
5. **[[Tasks]]** – past, present, and future tasks. 

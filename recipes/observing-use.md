---
name: observing-use
description: "Use when the requester asks to observe the product in use, to plan a session of observation, to turn the notes from one into an observation file, or to write down something a user said: 'observe a session', 'watch a session', 'usability test', 'what did they get stuck on', 'a user told me', 'user feedback'. It produces an observation file and changes to the insights file, and changes no code."
---

# Observing use

This ends in an observation file and changes to the insights file.

## Two forms

The **full form** is a moderated usability test. At each milestone listed in `WGM.md`, five or more people recruited to match those the product is for are given tasks while a moderator and a note-taker observe. This is what a project with research staff runs.

The **field form** is field observation. People who already use the product are observed one at a time in their real use of it, about five over a release. Whoever builds the product can run it alone, at a table.

Both produce the same file. `WGM.md` says which form the project runs. Observing your own use of what you build counts, marked as such. It is weaker evidence, though still evidence.

A report nobody planned counts too: a complaint, a question at the table, an email, an issue in the tracker. Write it as an observation, because if it is written into the backlog instead, it is one entry, and the pattern it was part of is never counted. The observation:

- is marked as reported rather than observed;
- names a role and nothing that identifies the person, since nobody was asked first;
- paraphrases what they said and, where they agreed to be quoted, cites their words, kept as "After" says;
- names the running commit, or says it cannot be known.

## Before

- **Ask.** A person is asked whether they agree to be observed, and told what is written down, where it goes and who can read it, and that it names a role, not them. Without that agreement, nobody is observed. Raw audio or video stays outside the repository, because it identifies the person, and the repository's history keeps it for everyone who clones it, now or later. A person who withdraws their agreement has their recordings and quotations deleted, and the observation stays.
- **Choose what to observe.** Choose a task the product is for, done for real where it can be. An assigned task shows what people can do, but real use shows what they do, and what they reach for instead.
- **Note the commit that is running.** An observation that names no commit cannot be checked against later.

## During

Write down each moment the product stops or slows a person. The moments fall into six kinds, so that the note-taker records rather than judges:

- asks how to do something
- reaches for paper, a phone or another product
- repeats the same action
- looks for something that is not there
- waits, and says so
- gives up, or someone does it for them

Write down as well what went well where it was expected not to. Help as late as the situation allows, because the moment before help is the observation.

## After

**One file per session, never edited afterwards**: the date, the commit, the form, each person as a role, and for each moment what they were trying to do, what happened and which kind it was. The observer's guess at the cause is a separate line, marked as a guess. What a person says afterwards goes below the moments, paraphrased. Where they agreed to be quoted, their exact words are kept with the recordings, in the place outside the repository that `WGM.md` names, and the observation cites them, so that a withdrawal never edits the observation. `WGM.md` says where the file lives.

**Then the insights.** An insight is a pattern named across observations, with the observations it rests on and how many people they cover. One observation is a hunch, and is written as one. The insights file is revised, but the observations never are.

## What comes out

- The observation file.
- Changes to the insights file, including, for a session after a change, which earlier moments recurred and which did not. That is the measure of "Good to use".
- A backlog entry for each moment that is plainly a defect, unless its report arrived as an issue, which is the entry, and a question for the requester where a pattern implies a choice.

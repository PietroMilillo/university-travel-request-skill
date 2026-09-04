# University travel request — a Claude skill template

A standing instruction file that prepares a university travel/expense request end to end:
budget pre-flight, the international branch, chartfield setup, expense lines, the agenda
attachment, and a set of stop conditions that halt rather than warn-and-continue.

**It never presses Submit and never attaches a file.** It hands you a filled request to
check instead of an empty one to assemble.

I wrote about why the redacted parts are the interesting ones, and why a private
workaround is worth less than a shared one, in an essay called *Twenty Minutes* on
[The AI Prof](https://theaiprof.substack.com). Direct link goes here when it publishes.

## This is a template, not my configuration

Every `[BRACKETED]` value has to be replaced with your own institution's system, policy and
defaults before it does anything useful. The chartfield codes, internal paths, department
defaults and policy language are stripped out. What is left is the shape: check the budget
first, branch by destination country rather than by the software's own foreign-travel flag,
know the traps before you hit them, and never let it submit without you.

## Use

Drop `SKILL.md` into `~/.claude/skills/university-travel-request/` (as `SKILL.md`), fill in
the brackets, then ask Claude to prepare a travel request.

## The traps are the point

The valuable part of a skill like this is not the automation, it is the written record of
every place your system misleads you. Mine had four. Yours will have four different ones.
**If you build one, keep that list separate from the automation and send it to whoever owns
the form.** That is the part that compounds, and it is the part I nearly kept to myself.

Pull requests with traps from other institutions' systems are welcome.

## Licence

MIT. See [LICENSE](LICENSE). Take it, adapt it, keep the notice.

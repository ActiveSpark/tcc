# Changelog

## v0.3.102

### Help
- Issue reports now go to TCC's public issue tracker on GitHub (github.com/ActiveSpark/tcc). The report window has **Open GitHub**, which opens a new bug report filled in with your version, platform and the end of the diagnostics log, and copies the full report to the clipboard. **Report Issue** in the command palette opens the same page. **Send** still sends your report straight to us, without a GitHub account. To remove the GitHub button, set `"issueTrackerUrl": ""` in `tcc-config.json`.
- The changelog's **View releases** button opens the GitHub Releases page, where each release's zip and installer are also published.

## v0.3.101

### Updates
- The update dialog has **Get release notes by email**: type your address and choose Subscribe, then open the link in the confirmation email. You get one email when each new version is out, and every email has a one-click unsubscribe link.
- The status bar's ⋯ menu has **Community discussions**, which opens TCC's GitHub Discussions (also in the command palette as Open Community Discussions).
## v0.3.100

### Phone
- **Tapping a Factory ticket on the phone opens its page** (phone 1.36, no desktop change). On the canvas and in a node's View all, a tap now opens the ticket's page (description, Go/Next/Yes/No, Delete); only its console button opens the console.
- **The phone terminal's top-right button shows the session's changes** (phone 1.35, no desktop change). It used to open a new session; that is still in the session switcher.

### Updates
- Settings → Auto Update has a **Usage count** row that says what TCC sends: once each, that it was first started and that its first sample factory ticket finished, with a random install id and its version, nothing else. Setting `"updateFeedUrl": ""` in tcc-config.json turns it off along with update checks.

## v0.3.99

### Factories
- **Share factory…** (in the factory's ⋯ menu) posts the factory as a link, such as relay.tcc.activespark.io/f/Ab3dEf7hJk, and gives you an image of its canvas to post with it. Anyone with the link sees its nodes and prompts and can open it in TCC. Its folders, ticket sources, plugin settings, engine and base branches are left out, and so are its tickets. Sharing needs a TCC Cloud sign-in, and each account can share 20 factories a day.
- **Import from link…** pastes a shared factory's link. **Open in TCC** on a link's page, or in the site's new workflow gallery (tcc.activespark.io/workflows), does the same when TCC was installed with the installer or `--install`. Before anything is imported, TCC shows every prompt and every plugin the factory uses, flags plugins that are not installed, and points out settings that widen what its prompts reach (a tickets node without worktrees, nodes that send console output to the engine): a shared factory's prompts are typed into AI sessions on your machine. A shared factory never brings Claude's skip-permissions mode along. It then asks for the factory's folders as Import factory… does. An imported factory never starts tickets on its own.

## v0.3.98

### Factory
- **Share this week's stats…** (in the factory's ⋯ menu) draws a card of the last 7 days, e.g. "12 tickets shipped by 3 agents, 41 commits": tickets that reached an end node, the most agents that worked at once, and your commits in the factories' repos. Repo names and ticket titles appear on it only when you switch them on. **Save PNG…** saves the picture; **Copy link** copies a link to the TCC site to post with it.

### Cloud connect
- **Invite a friend**: your account page shows a referral link. When someone signs up through it, verifies their email and connects a device through Cloud connect, you both get 1 GB more cloud data that month (on a trial too). Once per person, up to 5 rewards a month; signing yourself up again does not count.

## v0.3.97

### Factories
- **A ticket's AI session is named after its ticket**: a session Factory starts for a ticket shows as "TKT-139 Ticket and session name match" (or just "TKT-139" when that is its title) in the sessions panel, on its tab and in notifications, instead of the CLI's own title. Sessions started before this release keep their names, and a session you renamed yourself is never renamed.

## v0.3.96

### Factories
- **Try the Factory with a sample project**: on first launch TCC offers to make a small git repo in Documents\TCC Sample (a to-do page) with three tickets and a ready workflow: Implement, Review, a Yes/No you press, then Merge. It needs no decision engine. With Claude Code or the GitHub Copilot CLI installed, **Start the first ticket** starts it and you watch its AI session work in its own worktree. Without either, the card shows how to install one, with copy buttons, and can set the sample up for later. **Don't show again** hides it for good, and so does a workflow of your own. The command palette's "Try the Factory with a sample project..." brings it back.

### Privacy
- TCC sends two anonymous counts to its relay, once each: its first launch, and the first sample factory ticket that finishes. Each carries a random install id, the event and the version, and nothing else. `"updateFeedUrl": ""` in tcc-config.json turns them off, along with update checks.

### Phone
- **Links in the phone terminal open when you tap them** (phone 1.34, no desktop change). Tap an http or https address shown in a session and it opens in your browser, even when it wraps onto the next line. A tap anywhere else still shows or hides the keyboard.

## v0.3.95

### Factories
- **Drag tickets between nodes on the phone** (phone 1.32): on the phone's Factory canvas, **hold a ticket and drag it onto another node** to move it there, as you drag tickets on the desktop. A long press on a ticket row now picks the ticket up; hold a node's header (or use Settings) to open its settings. The node it would land on is outlined, and the view scrolls when you hold the ticket near an edge. Sessions still move off their session node only on the desktop, which asks for their description first; holding one on the phone says so instead of opening the node's settings. This was built for v0.3.88 but left out of that release. Phones move tickets through the protocol's revision 23 (`move` Factory action); update the desktop for this.

### Phone
- **The "Claude is waiting for you" reply strip no longer flashes on and off** while you use a session on the phone (phone 1.33, no desktop change). Showing the strip no longer resizes the desktop session (which made Claude redraw and hid the strip again in a loop), and it appears only once Claude has been waiting for 3 seconds with no typing on the phone.

## v0.3.94

### Install
- **winget and Scoop**: TCC can be installed with `winget install ActiveSpark.TCC` or from the ActiveSpark Scoop bucket, once the winget-pkgs PR is merged and the bucket repo exists. Each release regenerates both manifests (`packaging/`).
- **A silent install (winget) no longer starts TCC**; the normal installer still opens it when it finishes.
- **"Apps and features" shows the version TCC updated itself to**, so winget sees the real version and won't reinstall an older one over it.

## v0.3.93

### Factories
- **Engine errors no longer fail tickets**: when the decision engine times out, is busy, can't be reached or rejects a request, a categorise or switch node keeps the ticket and asks again by itself (after 15 s, then doubling up to every 5 minutes) until it answers. The history notes the error once.
- **Tickets that already failed on a categorise or switch node are asked again when the app starts**, so ones failed by an engine outage carry on without a Retry.

## v0.3.92

### Factories
- **Switch nodes ask the engine for tickets already waiting there**: turning on a switch (decision) node's engine check now sends the tickets held on it to the engine, when the workflow is saved and when the app starts. Before, they stayed held for Yes or No.
- **laya gets one request at a time**, so many tickets checking at once queue inside TCC instead of overloading the local engine until every check times out.

## v0.3.91

### Factories
- **Paging in the grouped view** (desktop and phone 1.31): each node lists its first 10 tickets; a node with more shows **View all N tickets**, which pages through them 25 at a time with **Previous**, **Next** and **Show less**. Finding a ticket (Next ticket, opening it from elsewhere) turns to the page it is on.

## v0.3.90

### Factories
- **Ticket page on phones** (phone 1.30): in the Factory's grouped view, tapping a ticket opens its page: title, where it is, its description, its Go / Next / Yes / No buttons, **View console**, and **Delete ticket** (asks first, as on the desktop; the worktree and branch are kept). The console opens only from View console or the row's console button, no longer from a tap on the ticket.
- Phones read a ticket's description and delete tickets through the protocol's revision 22 (`describe` and `delete` Factory actions). Update the desktop for this; an older desktop shows the page without a description or Delete.

## v0.3.89

### Phone
- Paired phones (phone 1.29) can **show a session's git changes**: in a terminal's menu, **Show changes (git diff)** lists the changed files of the session's folder (Unstaged, Staged or Branch, as the desktop's diff review) with their added and removed lines. Tap a file to see its changes.

## v0.3.88

### Terminals
- **Speech to text**: every terminal pane's title bar has a microphone button (left of the diff button, shown while the pane is focused or hovered). It focuses that pane and opens Windows voice typing (Win+H); what you say is typed into the terminal. Click it again, or press Win+H, to stop (while it listens, a click on another pane's mic stops it too).
- Terminals now accept text from input methods (IMEs), which is how voice typing delivers what it heard. A composition is shown in the input method's own window, not inline.
- On phones (phone 1.28), the key row under a terminal has a microphone key. Android's speech recognizer listens and the words are typed into the session, without Enter, so you can check them before running.

## v0.3.87

### Factories
- **Plugins** add your own node types that connect tickets to other services, such as pulling an issue from Jira. Put a plugin's folder (a `plugin.json` and its script) in `factory\plugins` in TCC's data folder. Its nodes are then listed in the canvas's Add menu after the built-in kinds. Each ticket that arrives at a plugin node runs the plugin's command on this desktop. The command can change the ticket's title, description and status, and it chooses the output the ticket leaves by. A plugin node's settings appear in the inspector. See docs/FACTORY-PLUGINS.md and the example Jira plugin in docs/plugins/jira.
- Plugins run only on the desktop. Paired phones (phone 1.27) can add plugin nodes, change their settings and follow their tickets without installing anything.

## v0.3.86

### Factories
- A ticket's **Files** box is now a drop zone: drag files from Explorer onto it to attach them (it lights up while you drag). **Attach…** still picks files. The same applies when you drag a session out of its node.

## v0.3.85

### Factories
- Every node has **Notify me when a ticket arrives here** (off by default). With it on, the desktop and paired phones (phone 1.26) show a notification when a ticket moves onto that node or is new on it (a new ticket on a tickets node). Clicking the desktop notification opens Factories.
- Phones now notify only for those nodes, instead of for every move. Paired with an older desktop, they still notify for every move.
- Terminals running a Factory ticket's AI session no longer raise their own "Session Ready" / "Approval Needed" notifications; Factory's "needs your input" notification still shows.

## v0.3.84

### Factories
- The docked Factories panel can now be dragged wider than half the window: it stops only where the terminals keep 30% of the width (or 360 px), as it already did on narrower windows. It was capped at 1200 px before, which on a wide screen kept the terminals at about half.

## v0.3.83

### Factories
- The **Expand to full window** button is gone.
- In the separate Factories window, **Dock Factories in the main window** puts it back in the main window and brings that window forward. Closing the separate window now closes Factories instead of docking it back.

## v0.3.82

### Factories
- Paste a screenshot into a ticket's description (Ctrl+V) and it is saved in the ticket's folder as `<ticket id>-<guid>.png` and added to the ticket's files. Text pastes as before.
- A ticket's files are now shown as chips: click **Attach…** to pick one or more files, and × to take one off the ticket (the file itself is kept). Files inside the tickets folder are stored relative to it, others by full path. The same applies when you drag a session out of its node.

## v0.3.81

### Factories
- The grouped view lists ticket nodes first, with session nodes after them and end nodes last. Session nodes start folded to their heading. Click a node's heading (or tap it on the phone) to fold or unfold it, and a ticket you jump to by search opens its node. Phone app 1.25.

## v0.3.80

### Factories
- An action node no longer leaves its prompt pasted but unsent. If the AI session hasn't started a turn and the prompt is still in its input box, Factory presses Enter again every few seconds. The run history notes "the prompt was still in the input box: submitted it again". If three more tries don't send it, the ticket fails with "The prompt was pasted but not submitted" so you can retry it, rather than sitting in Acting.

## v0.3.79

### Factories
- Factory is now called Factories: the status bar button, start page card, panel and window title ("TCC - Factories"), command palette (**Open Factories**), keyboard shortcut list and exit and update warnings. One flow you draw is still a factory. The phone says Factories too, on the Factories page and on each machine's Factories card in Sessions (phone app 1.24). Ctrl+Alt+B and the .workflow.json files are unchanged.

## v0.3.78

### Factory
- With the Factory open in a separate window, a ticket's session button now brings the main window to the front (restoring it if minimised) so you see the session straight away.

## v0.3.77

### Factory
- Grouped view: see every node's tickets as a list instead of the canvas. On the desktop, click the list button in the Factory top bar (the grid button switches back); on the phone, tap the four-squares button that used to show the whole factory (phone app 1.22). Each node shows its name, ticket count and settings button, then all its tickets with their Go, Next, Yes and No buttons and session button. Clicking a ticket opens it as on the canvas, and Next ticket and search scroll to it. The phone remembers which view you used last.

## v0.3.76

### Factory
- The start page's Factory card acts like a button: the pointer becomes a hand over it and the card brightens. **New session** and the previous-session rows show the hand and a hover highlight too.

## v0.3.75

### Phone
- Work on the Factory while the desktop is offline (phone app 1.21). The phone keeps the Factory as it last saw it, even after the app is closed, and a line over the canvas says the desktop is offline. A new ticket or session says "This ticket will be sent the next time HOME-PC is online"; Yes and No say your answer will be applied, if still relevant, when the desktop is connected again; Go, Next, new nodes and node settings queue the same way. When the desktop is back the phone sends them in order and says how many it took, naming any it refused (such as a ticket that has moved on). Opening a ticket's session still needs the desktop online. The desktop itself is unchanged; no desktop update is needed.

## v0.3.74

### Factory
- The mouse wheel zooms the workflow canvas in and out about the cursor; it no longer scrolls up and down. Drag the empty canvas to move around, and Shift+wheel (or tilting the wheel) still moves it sideways. Ctrl+wheel and touchpad pinch zoom as before.

## v0.3.73

### Factory
- End nodes close the ticket's AI session. **Close session** is on by default and waits 2 minutes (**Delay**, 120 seconds) after the ticket arrives; turn **Delay** off to close it as the ticket arrives, or turn **Close session** off to leave it open. Opening the session while the ticket sits on the end node (Open session, its tab, the palette or sessions panel, or from the phone) keeps it open; a ticket dragged away that reaches an end node again closes as before. The ticket keeps its AI session, so Open session resumes it later. The phone's node settings show the same options (phone app 1.20).

## v0.3.72

### Phone
- Check and install the desktop's update from the phone (phone app 1.19). In the Desktops tab, tap the connected desktop's **⋮**, then **Desktop update**. The page shows the installed version and whether a newer one is out; **Check for updates** checks now and downloads it, and **Install and restart** restarts the desktop into it. The phone reconnects by itself. When AI sessions or factory runs are working, the phone asks first: **Update now** or **When the factory is idle**. A development build is never updated from the phone. Desktops older than v0.3.72 say to update once on the desktop.

## v0.3.71

### Factory
- Copy a node with **Ctrl+C** and paste it with **Ctrl+V**, in the same factory or another one. The paste is a new node with the same settings and a fresh id, unconnected, down and to the right; pasting again places the next copy further down. A tickets or session node pastes only where it has a ticket source to share, as Duplicate does.

## v0.3.70

### Phone
- Sessions that run a Factory ticket show a factory icon on the phone's session list (phone app 1.18). Tapping one opens the Factory on that ticket: the right factory, zoomed to the ticket's node with its row outlined (or a note when only View all lists it). Tap the ticket there to open its terminal. If the phone has not had the desktop's Factory yet, the tap opens the terminal as before.

## v0.3.69

### Phone
- Change a Factory node's settings from the phone, as in the desktop's side panel (phone app 1.17). Tap a node, then **Settings** at the top right of the canvas, or press and hold the node. Each kind shows the fields the desktop shows for it: the name; a tickets node's ticket source, repo directory, base branch and Create worktree; a session node's folder and repo directory; a delay's wait; a wait node's condition and time limit; a decision's automatic check; the question or prompt and what the engine also sees; a categorise node's categories (rename, reorder, add, remove: the wires follow); an action's completion check; and N at a time. **Save** sends only what you changed, so a field changed on the desktop meanwhile is kept, and the desktop takes it as one change that Ctrl+Z there undoes. A new ticket source folder is still added on the desktop (Browse…). On a desktop older than v0.3.69 **Settings** says to update it.

## v0.3.68

### Phone
- The phone notifies you when a Factory ticket moves to another node (phone app 1.16): "TKT-12 moved to Review", with the ticket's title, the move and the workflow. It arrives with the app closed, a ticket's next move replaces its notification, and tapping it opens the Factory. Turn them off under Android's notification settings for TCC, channel **Factory tickets**. It works with any desktop version that has the phone Factory.

## v0.3.67

### Phone
- The New ticket form's description box has a microphone button at its bottom right (phone app 1.15). Tap it and speak: Android's speech recognizer listens and what it heard is added to the end of the description, which you can then edit. It works with any desktop version, since the phone does the listening and sends only the text.

## v0.3.66

### Phone
- Add nodes from the phone's Factory, as on the desktop (phone app 1.14). Tap **+ Node** at the top right of the canvas to add one in the middle of the screen (just below any node already there), or press and hold on empty canvas to add one there. The list is the desktop's Add menu: Decision, Categorise, Action, Delay, Wait, End, Tickets and Session. If the desktop has the factory open, the new node shows there at once, and Ctrl+Z on the desktop takes it back out. On a desktop older than v0.3.66 **+ Node** says to update it.

## v0.3.65

### Phone and watch
- Pressing **Next**, **Yes** or **No** on a ticket from the phone's Factory canvas moves the ticket on the phone straight away. It used to sit on its old node for up to two seconds.

## v0.3.64

### Phone
- The phone's Factory has a **+** in its top bar, left of the zoom button (phone app 1.13). Tap it, choose Ticket or Session, then the node to add it to (asked only when the factory has several), and fill in the form. A new session asks only for its name, as on the desktop, and is numbered SES-1, SES-2 and so on. Adding sessions from the phone needs this desktop version; an older one says to update.

## v0.3.63

### Phone
- Tapping a connected desktop in the phone's Desktops tab opens its Factory (phone app 1.12). A desktop that is not connected still opens its actions, and every desktop card has a **⋮** button for Host settings, Reconnect and Forget.

## v0.3.62

### Phone
- Every tickets node on the phone's Factory canvas has a **+** in its header, left of the ticket count, as on the desktop (phone app 1.11). Tap it to add a ticket. A tickets node's View all has the same **+**. On a desktop older than v0.3.56 the **+** says to update it instead of not being there at all. The keyboard comes up as the New ticket form opens.
- Tap a node to select it (it gets an accent outline); double-tap a node to zoom to it. Every zoom to a node now shows all of it instead of cutting its bottom off, and the zoom button zooms to the node nearest the middle of the screen.

## v0.3.61

### Phone and watch
- Tapping a ticket's "view session" button on the phone's Factory canvas now opens its session on the desktop, starting it when it has none, just as the desktop's own button does, and then shows its terminal on the phone (phone app 1.10). It used to say "no terminal yet".

## v0.3.60

### Phone
- The phone's Factory **Next** skips sessions, as the desktop's does, even when the desktop is older than v0.3.55 (phone app 1.9).

## v0.3.59

### Phone
- The phone's Factory switches factories with a button naming the shown one instead of a row of chips (phone app 1.8). Tapping it opens a scrolling list of every factory, the shown one ticked.

## v0.3.58

### Factory
- Factory now calls each workflow a factory everywhere it shows the word: + New factory, Factory settings, Open/Import/Export factory, the ← Factories back button, messages and hints. The phone says factory too (phone app 1.7). Factory files keep the .workflow.json extension, so existing ones open as before.

## v0.3.57

### Factory
- An untitled ticket takes up to 50 characters of its description as its title (was 25), and no longer cuts the last word in half: it runs on to the end of that word (up to 300 characters, the most a typed title takes). The title placeholder shows the same.

## v0.3.56

### Phone
- You can add Factory tickets from the phone (phone app 1.6). Open a tickets node's View all and tap **+**: write what needs doing, optionally a title, and tap Create. The desktop saves it in that node's ticket folder with the next TKT number, as its own New ticket does, and it shows on the phone at once. The desktop needs this version (protocol revision 14); with an older desktop the **+** does not show. If the answer is lost and you tap Create again, it does not make a second ticket.

### Factory
- A New ticket form left open no longer overwrites a ticket added meanwhile (from the phone or an editor): the ticket number is picked when you press Create, after every .tkt file in the folder.

## v0.3.55

### Phone and watch
- The phone's Factory has a **Next** (next ticket) button that steps through the tickets as the desktop's does, closing up on each one's node with its row outlined (phone app 1.5). A zoom button beside it closes up on the current node again, the way the screen opens.

## v0.3.54

### Factory
- Searching tickets also matches their descriptions: the tickets list's search box and the top bar's search both find a ticket by words in its description too. A top-bar result found only through the description says "matched in description".

## v0.3.53

### Phone and watch
- When Claude (or Copilot) is waiting for you, the quick replies are now **Yes, go ahead**, **No** and **Ignore** (phone app 1.4). Ignore sends nothing. On the phone it hides the reply strip until the agent stops waiting; on the watch it closes the reply sheet.

### Website
- The phone and watch scenes show Yes, go ahead / No / Ignore.

## v0.3.52

### Phone
- The phone shows your desktop's Factory, drawn as the desktop draws it (phone app 1.3). On the Sessions screen, the Factory button on the Factory header opens the workflow canvas: the same nodes, sizes, wires, icons, ticket rows, dots, badges and View all, live. It opens close up on the ticket waiting for you. Drag to move around, pinch to zoom, and the top-right button shows the whole workflow. With several workflows, a chip per workflow switches between them.
- The canvas works as on the desktop: Go, Next, Yes and No run on the desktop (Next asks which output on a node with several), a ticket or its session button opens its terminal, and View all lists every ticket on the node.
- The desktop sends its Factory to connected phones over the LAN and the cloud relay (protocol revision 13). Older phones are unaffected.

### Website
- The phone and watch section no longer says the phone's Factory screen is coming soon.

## v0.3.51

### Auto Update
- Settings → Auto Update's "Update now" is now "Check now". When a newer version is found it downloads in the background and the button becomes "Install". While factory tickets are running, Install still asks whether to update now or wait until the factory is idle.

## v0.3.50

### Cloud account
- The cloud sign-in no longer drops on its own. It ends only when you sign out in the app, sign the device out on the relay, reset your password or leave the device unused for 90 days. Before, a lost refresh answer, or two TCC installs open at once, could sign you out.
- The relay's account page has a Devices tab listing your signed-in devices. "Sign this device out" warns first that the device can then no longer be connected to through the relay.

## v0.3.49

### Cloud account
- The "Email verified" page has a Sign in button that opens the Cloud account page.

## v0.3.48

### Cloud account
- Signing in on the relay's account page works behind the TLS proxy. Before, every sign-in there was refused as "sent from another site".
- Accounts listed in the relay's RELEASE_UPLOADERS can publish a release from the account page: upload latest.json with the signed zip, the installer and any apk. The relay checks each file against the SHA-256 that latest.json signs and publishes latest.json last.

### Website
- A Sign in button in the menu bar and the mobile menu opens the Cloud account page.
- The installer button always downloads the newest installer.

## v0.3.47

### Factory
- On a session node, each session's dot shows what its AI session is doing, the same colours as the AI sessions list: blue thinking, amber running a tool, red needs approval, green waiting for you, grey idle or closed. The dot pulses while the session is busy, and the row's hover preview says the status in words. Tickets on other nodes still show their run state.

## v0.3.46

### Factory
- Esc no longer closes Factory, docked, as an overlay or in its own window. Close it with its ✕ or the Factory toggle. Esc still closes menus, dialogs, the diff review and the transcript, and on the canvas it cancels an edge drag and closes the panels open over it.

## v0.3.45

### Website
- The website's arcade is three interactive machines drawn like the app: Factory (a ticket rides a workflow to Done; press Go and Next when they blink), Session node (start a session in a project's node, close it, resume it later) and Manual review (open the diff from a ticket's terminal, leave notes, send them to Claude). The old game arcade and the Player 2 section are switched off.
- A new phone and watch section plays one story on both: Factory alerts land on the watch, and Open on phone, Next and Yes play out on the phone. It has download buttons for the Android and Wear OS apps.
- The download page's buttons no longer overflow their cards.

## v0.3.44

### Status bar
- The Report button reports a bug or requests a feature. Its modal has Bug and Feature buttons and a box to describe it; Send delivers the text with your TCC version and platform to the TCC relay, which records it (never the diagnostics log). If sending fails, your text is copied to the clipboard. Copy report and the issue-tracker button still work as before. The `feedbackUrl` setting points Send at another relay; `""` hides it.

## v0.3.43

### Exiting
- Exiting TCC while work is happening asks first: when AI sessions are working (thinking or running a tool) or Factory runs are deciding or acting, the window's close button (when it quits rather than hiding to the notification area), the notification icon's Exit and Restart & Update show "Exit TCC?" with what would be interrupted. Windows shutdown or log-off never asks.

## v0.3.42

### Factory
- Tickets have an **Auto start** toggle (off by default) in the ticket form, saved as `autostart: yes` in the `.tkt`. A ticket with it on starts by itself as soon as Factory sees it with no run: on Create, or when a `.tkt` file lands in the tickets folder while Factory has its workflow loaded. It starts once; a finished or failed ticket is not started again. Sessions are never auto-started.

## v0.3.41

### Terminals
- Zoom is per terminal and lives on each pane's last-prompt bar: − and + step it, the percentage resets it. Ctrl+= / Ctrl+- / Ctrl+0 zoom the focused terminal, Ctrl+wheel the one under the pointer. The status bar no longer shows the zoom, and the Set Zoom dialog is gone.
- Settings → Appearance → Font has a Default zoom (50-300%): the zoom new terminals open at, and what Ctrl+0 returns to.
- The last-prompt bar drops its Ping, All prompts and Prompt editor buttons; Ping stays in the session menu, Ctrl+Shift+K shows all prompts and Ctrl+Alt+E opens the prompt editor.

## v0.3.40

### Updates
- Auto update never downgrades: TCC now knows its real version (it had been reporting 0.3.0, so an older release looked newer), and a downloaded update installs only when its tcc.exe really is newer than the running and installed copies. A package that is not newer is turned down and not downloaded again.
- Restart & Update while factory tickets are deciding, acting or queued asks first: Update Now, or When Idle to restart once the factory has nothing running. Settings → Auto Update shows the pending update, with Cancel.

## v0.3.39

### Phone
- The phone shows the Factory's tickets: sessions running a ticket are listed in a Factory section at the top, each card saying its ticket and status ("TKT-56 · Working", "Needs your input"), on the local network and through the cloud alike. Searching for a ticket id finds its session. Needs phone app 1.1.
- The download page offers the Android phone app (.apk) beside the Windows installer and zip.

## v0.3.38

### Factory
- A node added to a workflow pops in from its centre: a quick grow-and-fade that settles in about a sixth of a second.

## v0.3.37

### Factory
- The workflow inspector scrolls with the wheel anywhere over it: over the gaps between its fields, and over a prompt box whose text fits (a prompt box that can scroll passes the wheel on once it reaches its end).

## v0.3.36

### Factory
- Resting the pointer on a ticket in a node for a second and a half shows a preview: its id and title, why it failed (when it did), and the first few lines of its description.

## v0.3.35

### Factory
- The ticket form remembers what you typed when you close the tickets sheet: New ticket (or Edit) on the same node brings it back. Cancel throws it away; an Edit draft is dropped if the ticket changed since.
- The title sits below the description and is optional: its placeholder shows the description's first 25 characters, which become the title when none is typed.
- Cancel and Create sit at the right of the form.

## v0.3.34

### Terminal panes
- A diff button (±) sits left of the focus/grid button on a pane's title bar. It opens the diff review for the pane's repository, like the pane menu's "Diff review".

## v0.3.33

### Factory
- The launch page shows a Factory card left of the sessions to resume: a factory illustration, "Run tickets through AI workflows" and an Open Factory button (Ctrl+Alt+B). Clicking the card opens Factory. The card is left out when the window is too narrow or too short for it.
- When Factory fills the window, is expanded to full window or is in its own window, it has no header bar: its open-in-a-separate-window, expand / restore and close buttons sit at the right end of the workflow toolbar. Docked beside terminals it keeps its header.

## v0.3.32

### AI sessions
- Prompts the Factory pastes into a Claude Code session show as the pasted text. Session titles, prompt search and the transcript no longer show the <pasted_content> wrapper tags Claude Code stores around pasted text.

## v0.3.31

### Diff review
- Ctrl+F finds text in the file the diff review shows, with the terminal's find bar: match case, whole word and regular expression toggles, the match counter, and Enter / Shift+Enter (or the arrows) for the next and previous match. Every match is highlighted and the current one is scrolled into view. The search carries over when you pick another file. Esc closes the find bar; the next Esc closes the review.

## v0.3.30

### Factory
- A Decision node has an Automatic check toggle in its settings. Off, tickets on it wait until you press Yes or No; on, the decision engine answers its question as before. A new Decision node starts with the check off; Decision nodes in saved workflows keep deciding automatically. Tickets already waiting when you turn the check on stay for Yes or No.
- Tickets on a Decision node have Yes and No buttons in place of Next, which send the ticket out by that output.

## v0.3.29

### Status bar
- The Factory button is now the first button on the left of the status bar.
- The Factory, Dirs, Explorer, Sessions and Worktrees buttons look pressed while their panel is open (Factory also while it is collapsed, over the terminals or in its own window).

## v0.3.28

### Factory
- A new Wait node starts with its condition off: tickets on it wait for Next until you turn the condition on. Wait nodes in saved workflows keep their setting.

## v0.3.27

### Factory
- Several tickets nodes can take tickets from the same source folder. Each of them lists the source's tickets that have not started, and Go (or dragging the ticket off the node) starts it from that node, with that node's repo, base branch and worktree settings, so the same tickets can enter the workflow at different points. Each node keeps its own "N at a time" limit. Tickets and session nodes with a source can now be duplicated; the copy shares the source. A tickets node and a session node still cannot share one.

## v0.3.26

### Terminal
- Scrolling the mouse wheel over a full-screen program (Claude Code, less, vim) clears the text selection, instead of leaving the highlight on screen while the program scrolls its text away from it. Scrolling back through the terminal's own history keeps the selection on its text, as before.

## v0.3.25

### Factory
- Export workflow… (in the workflow ⋯ menu) saves a copy of the current workflow to share, with this machine's repo directories and ticket folders taken out.
- Import workflow… reads a workflow file and asks for each repo directory and ticket folder it uses, with Browse… to pick them; one left blank can be set later. The copy is added to the list with its own id, and the picked file is left unchanged.

## v0.3.24

### Factory
- A node's tickets list (View all) scrolls with the mouse wheel anywhere over it, not only over a row's text and buttons.
- The tickets list has a search box: type to filter its tickets by id, title or status.
- A search button in the Factory's top bar finds nodes (by name, kind or prompt) and tickets on any node (by id or title) as you type. Up/Down and Enter, or a click, select the node and centre it, or select the ticket on the canvas or in its node's tickets list.

## v0.3.23

### Factory
- Dragging a node, a group, a ticket, a connection, an edge end, a resize grip or a selection box close to the edge of the workflow canvas scrolls the canvas that way. It scrolls faster the nearer the edge and keeps going while the pointer rests there, and the dragged item stays under the pointer. Zooming with Ctrl+wheel mid-drag no longer makes a dragged node jump.

## v0.3.22

### Text fields
- Dragging the mouse across a text field selects text, as in any text box (the ticket title field in particular, where a drag only moved the caret). The selection follows the pointer out of the field until the button is released; the click that focuses a field still selects all of it, and double-click and Shift+click work as before.

## v0.3.21

### Terminal
- Text on a light theme's background is always readable. Colours programs write assuming a dark terminal, such as white and bright white, are darkened until they reach a 4.5:1 contrast with the pane (they were nearly or fully invisible in Solarized Light, Catppuccin Latte and Rosé Pine Dawn), and accent colours below that ratio are darkened slightly. Dim text and dark themes are unchanged.

## v0.3.20

### Layout
- Panes no longer float. Dragging a pane snaps it into the layout (split beside a pane, swap, or a full edge); dropping anywhere else does nothing. Ctrl+Shift+U, "Float pane" in the pane menu and "Toggle Float" in the palette are gone. Floating panes in a saved session or named layout from an older version join the layout when it loads, and an old toggleFloat entry in keybindings.json is ignored without a warning.

## v0.3.19

### Factory
- Next ticket skips sessions: it steps through tickets only, leaving out sessions both on their session node and after they are dragged onto another node.

## v0.3.18

### Settings
- A new Auto Update page at the bottom of Settings shows the current version, the update status, the update server (relay.tcc.activespark.io), whether automatic checks are on, and when TCC last checked. Update now asks the server for the latest version and, when it is newer, downloads it and restarts TCC into it. A development build opens the update dialog instead. The palette has "Settings: Auto Update".

## v0.3.17

### Factory
- Undo and redo in the workflow editor: Ctrl+Z undoes the last change to the workflow (moving, resizing, adding, duplicating, renaming or deleting a node; connecting, reconnecting or deleting a connection; a node or workflow setting) and Ctrl+Y or Ctrl+Shift+Z redoes it. The ↶ and ↷ buttons in the top bar do the same. Each workflow keeps its own history; typing in a setting is one step.

## v0.3.16

### Factory
- A Wait node can have a time limit (off by default). Switch on Time limit in its settings and set the seconds: a ticket held there moves on by next once it has waited that long, even if the condition never answers yes. Next still moves it on sooner. With the condition off, the node reads "Waits for Next, at most 5 min".

## v0.3.15

### Factory
- Hold Shift or Ctrl on the workflow canvas to select, whichever of Pan or Select is chosen: drag a box to add nodes to the selection, or click a node to add it or take it out. Releasing the key goes back to the chosen mode.

## v0.3.14

### Factory
- Browse… beside a folder field opens the folder picker in the folder already in the field, when that folder exists. Browse beside a ticket source opens in the chosen source's folder (the workflow's source when the node inherits it).

## v0.3.13

### Factory
- A Next ticket button on the workflow toolbar selects the next ticket not on an end node and moves the canvas to it. It walks the nodes along the arrows from the tickets node (nodes no arrow reaches come last), each node's list top to bottom, and wraps round, so pressing it again and again visits every ticket that is still in progress. It carries on from the selected ticket or node; when the ticket it was on has moved on, it carries on from that ticket's node rather than starting over. A ticket below the rows its node shows is highlighted in the node's tickets sheet.

## v0.3.12

### Factory
- Each node's header has a menu button (⋯) right of its cog: Settings, Duplicate and Delete. Duplicate adds a copy of the node, with all its settings but no connections, next to it (not for tickets and session nodes, whose copy would share their ticket source). Delete asks first when tickets are on the node, and is unavailable on the last tickets node.

## v0.3.11

### Factory
- A Categorise node's categories can be reordered with the ↑ and ↓ buttons beside each one in the inspector. The node's outputs move with them, and their connections stay attached.

## v0.3.10

### Factory
- Long titles in the side panels are no longer cut off by the buttons to their right. A ticket's title in the tickets list, and a node's or workflow's name at the top of its settings, now wrap onto more lines beside the buttons, with a ticket's id leading its title.

## v0.3.9

### Diff review
- Long lines in the diff review are no longer cut off with "…": the code scrolls sideways with Shift+wheel, a tilt wheel or touchpad, the Left/Right keys, or the thin scrollbar along its bottom, while the line numbers stay put. Lines over 10,000 characters (minified files) show their first 10,000 and a " …".

## v0.3.8

### AI sessions
- A pane's new `claude` or `copilot` is no longer labelled with an older conversation that only looks busy. A Factory ticket's conversation, still waiting hours later, could be linked to a pane opened for something else, and the ticket's Open session then went to that pane. A pane now only takes a new conversation created about when its CLI started (within 30 seconds), as panes found by folder already did.

## v0.3.7

### Factory
- Opening a session no longer opens an unrelated AI session. Sessions share their repo folder, and a new session's pane was matched to a conversation by folder, so it could save someone else's conversation and open that one from then on. Every AI session Factory starts, Claude Code or Copilot CLI, now starts under its own id (`--session-id`) saved on the ticket, so nothing is matched by folder. Opening it again reopens that same conversation: even after its pane closed, after a restart, or before its first prompt. A Claude Code pane's startup command becomes `--resume` as it is typed once the conversation exists. Sessions that already saved the wrong conversation keep it.

## v0.3.6

### Status bar
- The terminal count includes hidden panes, so it matches the terminal list it opens. It used to read "0 terminals" when every pane was hidden, while the list showed them all. With floating panes the breakdown also names the hidden ones: "4 terminals (1 tiled, 1 floating, 2 hidden)".

## v0.3.5

### Factory
- Each node lists the ticket that arrived on it most recently first (by an output or a drag), instead of by the number in the ticket id. Tickets never started stay on top of the Tickets node.

## v0.3.4

### Factory
- Sessions on a session node can be opened: Open session in the list, or the session button on its canvas row. A session with no AI session yet gets a new one in its repo directory; one it already has is focused or resumed. Dragging it onto a node afterwards types into that same session.

## v0.3.3

### Factory
- A folder picked with Browse… on a tickets or session node (or the workflow's ticket source) shows its path straight away, instead of its source id (s1, s2…) until you clicked off and back on.

## v0.3.2

### Diff review
- A mode with no changes says "No changes" instead of showing "Loading changes…" forever.
- The review opens on the first of Unstaged, Staged and Branch that has changes (Branch when none do), instead of always on Unstaged.

## v0.3.1

### Automatic updates
- TCC updates itself from its own release feed on the TCC Cloud server. The installed copy (`tcc.exe --install`) checks 10 s after launch and then hourly, downloads a newer release in the background and offers Restart & Update; if you just quit, the update installs on the way out. A copy run from anywhere else updates only through Check for Updates.
- Only a package signed with TCC's release key installs, and only when the download matches its signed hash; anything else is discarded. A release without a valid signature offers its release page instead.
- `"updateFeedUrl": ""` in `tcc-config.json` turns update checks off; any other value replaces TCC's feed, as before.

### Factory
- **Session node**: holds command sessions instead of tickets (Add Session). New session needs only a name and an optional repo directory (else the node's, else the workflow's default) and writes a session file to the node's folder. The node has no output: drag a session onto another node, confirm its description and files, and it runs there in the repo directory itself, with no worktree, keeping the same AI session each time you drag it.
- **Create worktree** (on by default): switched off in a Tickets node's settings or the ticket form (`worktree: no` in the `.tkt`; a ticket's own setting wins), the ticket's actions run in the repo directory itself, on whatever branch it has checked out, instead of a worktree of their own. Such tickets share that checkout, so run them one at a time; their AI session is only ever found by its own pane or id, never by folder.
- **Several tickets at once**: Shift-click or Ctrl-click tickets in a node to select several, then drag any of them to move them all.
- **Ticket details**: double-click a ticket on the canvas to open its details.
- **Zoom**: Ctrl+wheel and touchpad pinch zoom the Factory canvas instead of the terminals.

### Terminal
- In panes that track the mouse, the drag-selection highlight follows the pointer.

## v0.3.0

### Factory
- Factory replaces the Backlog board. It opens from the same places: Ctrl+Alt+B, "Open Factory" in the command palette, and the Factory item in the status bar. It docks left or right, collapses to the edge, expands to the whole window or opens in its own window.
- The Backlog board, "Attach to focused agent" and the AI bar's Update Backlog button are gone. A keybindings.json entry for `openBacklog` now opens Factory.
- **Workflows**: draw a workflow on a node canvas. Every workflow starts at a Tickets node; add Decision (yes/no), Categorise (one output per category you define) and Action nodes from the right-click menu and wire their outputs together. A ticket that takes an unwired output is finished.
- **Tickets** come from a folder of `.tkt` files (a short header with id, title, status and referenced files, then the description). View on the Tickets node lists them; Start sends one through the workflow.
- **Decision engines**: Decision and Categorise nodes ask laya (runs locally: Engine settings → Download installs it, about 1.9 GB) or a jev endpoint where the ticket goes next. The engine sees the node's prompt and either the ticket metadata (id, title, status, description, repo directory and referenced files) or the ticket's title and description with the last 400 tokens (configurable) of its AI session console.
- **Actions** give each ticket its own git worktree and AI session (Claude Code or Copilot CLI), type the node's prompt into it (`{id}`, `{title}`, `{description}` and `{files}` are filled in) and move on when the turn ends. The ticket keeps the same AI session for the rest of the workflow, across restarts too.
- **Workflow files**: each workflow is its own `<Name>.workflow.json`, saved where you choose when you create it; the name follows the file, and renaming renames the file. Open workflow adds an existing file. Workflows from earlier builds move to their own files automatically.
- **Tickets on the canvas**: the Tickets and End nodes show how many tickets are there and the top 10, with View all. Click any node to see the tickets on it, and drag a ticket onto another node to move it there. Shift-click a second ticket in the same list to select every ticket between, or Ctrl-click to pick tickets one by one, then drag any of them to move them all. Double-click a ticket to open it: the tickets sheet opens on its details (title, description, files, repo directory) ready to edit.
- **Quick add**: a Tickets node's header has a + next to its cog; it opens the tickets sheet on the right with a New ticket form ready.
- **End node**: tickets that reach it stop there and stack up.
- **Node names**: double-click a node's title (or use Name in its settings) to name it; the name shows on the canvas, in the tickets lists and sheet titles. Empty goes back to the kind.
- **Delay node**: tickets wait a set time (Add Delay; seconds in its settings), showing the time left on each ticket, then move on by next; Next skips the rest of the wait.
- **Wait node**: tickets stay here until a condition is met (Add Wait). Like a Decision node it asks the decision engine a yes/no question, every 60 seconds by default, and moves the ticket on by next once the answer is yes. Turn the condition off and the node only lets a ticket go when you press Next on it.
- **Ticket commands**: every ticket has Delete (its .tkt file is deleted; its worktree and branch are kept) and Push to next step (pick the output when a node has several).
- **Completion check** on action nodes (on by default): while the AI session is quiet, the decision engine is asked every 60 seconds whether the work is done, so a ticket moves on even if the end of the turn is missed. The question and interval can be changed.
- **Base branch**: a new ticket branch starts from the repo's default branch (origin's HEAD, else origin/main, origin/master, main, master), fetched first, not from whatever the main checkout has checked out. A Base branch in the workflow settings (or a Tickets node's, which wins) sets it instead. Existing ticket branches are never changed; the run history notes the base used.
- **Needs your input**: when a ticket's AI session waits for you (its turn ended and the completion check said no, or a tool waits for approval), the ticket shows "Needs your input" in amber and TCC notifies once; clicking the notification opens the session. It goes back to working as soon as the session does.
- **Repo per ticket**: worktrees are made from the most specific repo directory set: the ticket's own (Repo directory in the ticket form, `repo:` in the `.tkt`), else the Tickets node's (Repo directory in its settings), else the workflow's Default Repo Directory.
- **Claude Code (dangerously skip permissions)** as a workflow's AI CLI: it never stops to ask before running a tool.
- **N at a time**: any node (but End) can limit how many tickets it works on at once; the rest queue on it and go in longest-waiting first.
- **Canvas toolbar**: zoom out, the zoom percentage (click for 100%) and zoom in; a Pan/Select toggle, where Select drags a box to pick several nodes, then moves or deletes them together.
- View all spans the node's full width. Clicking a node closes the other open sheets. An action node's terminal starts hidden.
- Fixed: a Tickets node's Browse-picked repo directory was not saved; a ticket's repo placeholder now shows its Tickets node's override; a review action that runs a bare skill command (such as `/code-review`) now waits for its turn instead of passing straight through.
- Fixed: a ticket could stay on its action after Claude finished, when Claude had changed into a subfolder; and a brief gap in detecting the AI CLI could fail an action.

### Window
- Closing TCC hides it to the notification area, so terminals and Factory keep running; click the icon to bring it back, right-click → Exit to quit. Settings → System → "Close to notification area" turns it off.

## v0.2.0

### Cloud remote devices
- Reach this PC from anywhere through the TCC cloud relay, not only on the same Wi-Fi. Turn it on in Settings → Remote devices → Cloud and sign in; email verification, with a Resend link, is part of sign-in.
- Traffic between devices is end-to-end encrypted through the relay. Each device's key is pinned, and a new viewer must be approved from a fingerprint toast on this PC.
- **Connect to host** opens another PC's workspace in this window: its tabs and panes render here, keys and copy go to the remote pane, and saved hosts reconnect on their own.
- The phone and watch apps can use the cloud relay as well as the local network.
- Usage limits and the trial period show as notifications, with plain-language reasons when the cloud is unavailable.

### Remote clients
- Tab groups and dormant tabs are published to connected phones, watches and viewers.

## v0.1.6

### Chrome
- The status-bar tip uses the monochrome lightbulb icon instead of the colour emoji.
- The "Tabs" status-bar button is gone. Tabs are always shown at launch; Ctrl+Shift+B or "Toggle Top Bar" in the command palette hides them until the next launch.
- The expand button on a pane's title bar switches between focus and grid view instead of floating the pane. Floating stays in the pane's ⋯ menu and on Ctrl+Shift+U.

## v0.1.5

### Sessions
- The save icon on a launch picker row saves the session at once, without asking for a name. It is saved under its last-modified time (for example `2026-10-11 14-50-04`).
- "Open Saved Session..." lists the newest saved session first.

## v0.1.4

### AI sessions
- A Claude session whose turn has ended but still has background tasks running (shells, agents, monitors) now shows Running in background instead of Waiting for input, in the desktop UI and on remote devices.
- Background tasks that finish mid-turn, are stopped or are orphaned are cleared, and a timed monitor stops counting once its timeout runs out, so a session no longer stays stuck in the background state.

## v0.1.3

### Sessions
- Launch session picker: when TCC starts after a previous session, it asks first instead of restoring automatically. A big New session button sits above your last five unsaved sessions; click one to resume its terminals, layout and AI sessions. Starting a new session keeps the old ones.
- The save icon on a row stores that session under a name and takes it off the list. Open it again with the palette's "Open Saved Session...".
- When the list is full, the oldest session is outlined red: starting a new session will delete it.

## v0.1.2

### App chrome
- Plain monochrome icons: menus, the status bar, settings, the prompt editor and the pane AI bar draw Segoe Fluent Icons line glyphs in the text colour instead of colour emoji.

## v0.1.1

### Fixes
- Typed characters now appear in the command palette, the workspace rename field, menu text boxes and every other chrome text field; before, they were swallowed.

## v0.1.0

### App chrome
- **12 theme presets** (Catppuccin Mocha and Latte, Warm Dusk, Tokyo Night, Dracula, Nord, Gruvbox Dark, Rosé Pine and Rosé Pine Dawn, Solarized Dark and Light, GitHub Light) recolour the tab bar, status bar, menus, dialogs, panes and every terminal, including the 16 ANSI colours.
- Light themes get light chrome: hover washes, borders and the tab bar follow the theme instead of staying dark.
- A hand-edited theme derives its chrome from its own colours, and all 20 colours (bright ones included) can be edited in Settings → Appearance.
- **Tab groups** with collapsible headers, a member count and a coloured lane; groups are saved with the session.
- The tab context menu: rename, splits, focus mode, hide/wake, tab colours with a named swatch grid, colorize all, groups, tab bar position, new terminal and close actions.
- Status bar popovers for the terminal list and hidden panes, the `⋯` overflow menu, broadcast typing, zoom presets, this changelog and a report template.
- Settings: theme gallery, monospace font picker (fonts are found in the background and shown in their own face), font preview, tab options, Windows 11 Mica / Acrylic backdrop and opacity.
- Toasts with an icon, a dismiss button and a gentle fade.

### Terminal and layout
- Native Skia renderer with a glyph atlas, ligatures on request, `Ctrl+wheel` zoom shared by every pane.
- Splits, grid and focus modes, floating panes, workspaces, drag-and-drop docking, and session restore.

### Companion apps
- The embedded endpoint serves the phone and watch apps over an encrypted WebSocket with QR pairing.

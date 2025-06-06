# climbing-accident-reporter
Climbing accident reporter (a trial for a chat bot)

Purpose
  Create an anonymous Climbing Accident Reporter bot for the international mountaineering community (based on the AAC form). Its single in-depth topic—“Report Climbing Accident”—walks a user through every detail needed for a standard accident or near-miss report, then hands the data to Power Automate for storage or e-mail.

Core Topic: Report Climbing Accident
  Greeting & scope check – Welcome the user; ask if they want to report an Accident or a Near-Miss Incident.
  Date & time – Collect the accident date (YYYY-MM-DD) and approximate time.
  Location hierarchy – Municipality + state ➜ precise feature (mountain / wall / route / gym).
  People involved – Total number, number of fatalities (if any).
  Environment type – Quick replies: rock (free), ferrata, mountain ridge, forest/trail, river/waterfall, climbing gym, other.
  Stage of activity – Quick replies: ascent, descent / rappel, stationary on route, walking/approach, other.
  Weather & conditions – Options (sunny, cloudy, rain, fog, unknown) plus free-text notes.
  Immediate cause – Single-select list: fall, human error, bolt pulled, gear pulled, rockfall, lightning, slip, exceeded skills, equipment failure, lost, other.
  Contributing causes – Multi-select: no helmet, soloing, inadequate protection, exceeded skills, night, bad positioning, worn gear, group separated, other.
  Injuries – Multi-select or “none”: fatality, fracture, laceration, contusion, hypothermia, dehydration, psychological shock, other.
  Experience level – Little (<1 yr), Moderate (1-3 yrs), Experienced (>3 yrs), N/A.
  Narrative – Free-text: “Describe what happened. Use ‘Climber A’, ‘Climber B’ instead of real names.”
  Prevention tips – Free-text: “What lessons or techniques could prevent a similar event?”

Summary & confirmation – Show all answers; ask “Is everything correct?” • If No, let user edit a field. • If Yes, call the SubmitClimbReport action (Power Automate).
  Tone & UX
    – Friendly, concise, supportive.
    – Quick-reply buttons for lists.
    – Accept “skip” / “unknown” for any question (store as blank).
    – Validate obvious formats; reprompt twice, then allow skip.
    – Never request personal identifiers.

System messages
    • Help: “I collect anonymous accident details to improve climbing safety. You can type ‘skip’ if unsure.”
    • Cancel: “Understood. You can restart anytime by typing ‘report accident’.”

Integration
On successful confirmation, pass all captured variables (incidentType, accidentDate, accidentTime, municipality, preciseLocation, peopleTotal, fatalities, environmentType, activityStage, weather, immediateCause, contributingCauses, injuries, experienceLevel, narrative, preventionTips) to a Power Automate flow named SubmitClimbReport.


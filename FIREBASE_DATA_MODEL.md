# Campus Newsroom: Firebase Data Model

The first sync bridge stores all app data in:

```txt
newsroomState/living-stone-newsroom
```

That keeps pilot testing simple. For real school-wide production, split the data into these collections.

## Recommended Production Collections

```txt
users
writerProfiles
articles
articleVersions
teacherComments
evaluations
badges
userBadges
notifications
lessonProgress
practiceAttempts
practiceAssignments
certificates
certificateSettings
pressIdSettings
coverageTasks
coverageSubmissions
meetings
attendance
publicationIssues
activityLogs
```

## Role Access Plan

Student Writer:
- Read own drafts, feedback, certificates, badges, assigned tasks
- Create and update own unpublished articles
- Submit coverage materials assigned to them
- Read all published articles

Teacher / News Adviser:
- Read all student submissions
- Add comments, evaluations, feedback, and revision requests
- Award certificates if permitted
- Monitor writer progress

Editor:
- Read approved and revised articles
- Add quality review notes
- Schedule and approve publication

Publication Administrator:
- Manage users, categories, certificates, press IDs, coverage, archive, and final publication

Public Reader:
- Read only published articles.

## Storage Plan

Use Firebase Storage later for:

- Student profile photos
- Article photos
- Editorial cartoon image uploads
- Press ID templates
- Certificate logos and signature images
- Meeting or coverage attachments

## Why We Start With One Sync Document

The current app is a single-file HTML prototype. A one-document sync bridge lets us test real-time sharing quickly without rebuilding everything first.

After pilot testing, the next production upgrade should replace the one-document bridge with role-based collections and secure Firestore rules.


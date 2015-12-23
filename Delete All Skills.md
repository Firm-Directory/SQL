```sql
-- Note: This script will delete all Skills and related data
-- This is not officially supported. Use at your own risk
DECLARE @TranName VARCHAR(20);
SELECT @TranName = 'ClearSkills';

BEGIN TRANSACTION @TranName;
-- clean up notifications
DELETE FROM dbo.Notification where ReferencedSkillId is not null

-- delete Enhanced Skill content
DELETE FROM EnhancedSkills.SelfRating
DELETE FROM EnhancedSkills.Approval

-- delete links between Account and Skills
DELETE FROM dbo.AccountSkillEndorsement
DELETE FROM dbo.AccountSkillSuggestion
DELETE FROM dbo.AccountSkill

-- delete Skills
DELETE FROM dbo.Skill
DELETE FROM dbo.SkillCategory
DELETE FROM dbo.SkillRequest


COMMIT TRANSACTION @TranName;
GO
```

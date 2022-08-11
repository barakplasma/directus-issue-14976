1. download https://github.com/lerocha/chinook-database/blob/e7e6d5f008e35d3f89d8b8a4f8d38e3bfa7e34bd/ChinookDatabase/DataSources/Chinook_Sqlite.sqlite
1. npm init directus-project issue-14976
1. configure with sqlite
1. change package json to "directus": "9.14.5",
1. delete data.db
1. move chinook into directory and change .env
1. git commit 9.14.5
1. change package json to "directus": "9.15.1"
1. run npx directus database migrate:latest

Logs
```sql
michael@quris-michael:~/Projects/dir-sqlite/issue-14976$ npx directus database migrate:latest
11:23:20 ✨ Running migrations...
11:23:20 🔍 Enabling SQLite Foreign Keys support...
11:23:20 🔍 [1.170ms] select * from `directus_migrations` order by `version` asc []
11:23:20 ✨ Applying Update Notifications Timestamp Column...
11:23:20 🔍 [0.196ms] SELECT type, sql FROM sqlite_master WHERE (type='table' OR (type='index' AND sql IS NOT NULL)) AND tbl_name='directus_notifications' []
11:23:20 🔍 [0.126ms] PRAGMA foreign_keys []
11:23:20 🔍 [0.075ms] PRAGMA foreign_keys = OFF []
11:23:20 🔍 [0.453ms] CREATE TABLE `_knex_temp_alter537` (`id` integer PRIMARY KEY AUTOINCREMENT NOT NULL, `timestamp` datetime DEFAULT CURRENT_TIMESTAMP, `status` varchar(255) DEFAULT 'inbox', `recipient` char(36) NOT NULL, `sender` char(36), `subject` varchar(255) NOT NULL, `message` text, `collection` varchar(64), `item` varchar(255), FOREIGN KEY (`recipient`) REFERENCES `directus_users` (`id`) ON DELETE CASCADE, FOREIGN KEY (`sender`) REFERENCES `directus_users` (`id`)) []
11:23:20 🔍 [0.175ms] INSERT INTO "_knex_temp_alter537" SELECT * FROM "directus_notifications"; []
11:23:20 🔍 [0.207ms] DROP TABLE "directus_notifications" []
11:23:20 🔍 [2.389ms] ALTER TABLE "_knex_temp_alter537" RENAME TO "directus_notifications" []
11:23:20 🔍 [3.118ms] PRAGMA foreign_key_check []
11:23:20 🔍 [0.120ms] PRAGMA foreign_keys = ON []
11:23:20 🔍 [4.063ms] insert into `directus_migrations` (`name`, `version`) values (?, ?) [Update Notifications Timestamp Column, 20220801A]
11:23:20 ✨ Applying Add Custom Aspect Ratios...
11:23:20 🔍 [4.160ms] alter table `directus_settings` add column `custom_aspect_ratios` json []
11:23:20 🔍 [4.338ms] insert into `directus_migrations` (`name`, `version`) values (?, ?) [Add Custom Aspect Ratios, 20220802A]
11:23:20 ✨ Database up to date
```
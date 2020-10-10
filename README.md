self Referential Association

aniket = User.create(username: "aniket")
shivam = User.create(username: "shivam")
tiwari = User.create(username: "tiwari")
shikhar = User.create(username: "shikhar")
varun = User.create(username: "varun")

Follow.create(follower_id: shikhar.id, followee_id: varun.id  )

varun.followers

User Load (1.2ms)  SELECT "users".* FROM "users" INNER JOIN "follows" ON "users"."id" = "follows"."follower_id" WHERE "follows"."followee_id" = $1 LIMIT $2  [["followee_id", 6], ["LIMIT", 11]]
 => #<ActiveRecord::Associations::CollectionProxy [#<User id: 5, username: "shikhar", created_at: "2020-09-26 06:21:03", updated_at: "2020-09-26 06:21:03">]> 

shikhar.followers

  User Load (1.2ms)  SELECT "users".* FROM "users" INNER JOIN "follows" ON "users"."id" = "follows"."follower_id" WHERE "follows"."followee_id" = $1 LIMIT $2  [["followee_id", 5], ["LIMIT", 11]]
 => #<ActiveRecord::Associations::CollectionProxy []> 


shikhar.followees

  User Load (1.2ms)  SELECT "users".* FROM "users" INNER JOIN "follows" ON "users"."id" = "follows"."followee_id" WHERE "follows"."follower_id" = $1 LIMIT $2  [["follower_id", 5], ["LIMIT", 11]]
 => #<ActiveRecord::Associations::CollectionProxy [#<User id: 6, username: "varun", created_at: "2020-09-26 06:21:10", updated_at: "2020-09-26 06:21:10">]>

References: https://github.com/reireynoso/self_ref_practice

----------------------------------------------------------------

Active Storage setup

rails active_storage:install
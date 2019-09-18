-- 统计本人git项目代码数量，在某个时间段内

`git log --author="$(git config --get user.name)" --pretty=tformat: --since ==2019–09-01 --until=2019-10-01  --numstat | gawk '{ add += $1 ; subs += $2 ; loc += $1 - $2 } END { printf "added lines: %s removed lines : %s total lines: %s\n",add,subs,loc }' -`

-- 统计git项目中所有人的代码数量，在某个时间段内

`git log --format='%aN' | sort -u | while read name; do echo -en "$name\t"; git log --author="$name" --pretty=tformat: --since ==2019–09-01 --until=2019-10-01 --numstat | awk '{ add += $1; subs += $2; loc += $1 - $2 } END { printf "added lines: %s, removed lines: %s, total lines: %s\n", add, subs, loc }' -; done`

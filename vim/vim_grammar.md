# vim 的使用

## vim删除所有内容
两种方法：
  - 1、按下":"切换到命令模式然后输入%d并执行
  - 2、按下esc回到不编辑的状态（注意：不用按":"），然后输入gg dG
## vim批量替换字符

[vim字符替换](https://blog.csdn.net/v1v1wang/article/details/5418098)

- 将vivian字符替换为sky
  - 替换**所有**包含vivian的字符为sky

`:s/vivian/sky/g`


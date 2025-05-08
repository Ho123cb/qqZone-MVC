```md
表四：学习点清单 → 写在 docs/learning.md
每次卡壳/踩坑/优化后的思考，都记一条“微总结”：


- LocalDateTime 不能直接塞进 java.util.Date → 改用 java.time.LocalDateTime
- Thymeleaf 中访问 null 会抛异常 → 加 ?. 判断避免 NPE
- Controller 层要保证 session.userBasic、session.friend 必须不为空

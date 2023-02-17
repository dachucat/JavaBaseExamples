For generating table of contents in README.md
https://ecotrust-canada.github.io/markdown-toc/
(Replace double hyphens with single hyphens after generation)

<foreach collection="codes" index="index" item="code"
         open="(" separator="," close=")">
    #{code}
</foreach>
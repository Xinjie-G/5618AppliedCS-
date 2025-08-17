# 5618AppliedCS-
5618
cat \${BASE_CONFIG} \\
    <(echo -e '<ca>') \\
    \${KEY_DIR}/ca.crt \\
    <(echo -e '</ca>\\n<cert>') \\
    \${KEY_DIR}/issued/\${1}.crt \\
    <(echo -e '</cert>\\n<key>') \\
    \${KEY_DIR}/private/\${1}.key \\
    <(echo -e '</key>') \\
    > \${OUTPUT_DIR}/\${1}.ovpn

# Bioinformatics common files basic operations
 生物信息学中常见的文件例如fasta，bed等基本操作，例如读取，查询等
- fasta文件
~~~
#python下读取fasta文件,想要字典类型的话修改一下就行
sequences = []
seq_ids = []
with open(fasta_path) as f:
    for line in f:
        if line.startswith(">"):
            seq_id = line[1:].strip().split(" ")[0]
            seq_ids.append(seq_id)
            sequences.append("")
        else:
            sequence = line.strip().replace("U","T")
            sequences[-1] += sequence

id_seq_dict = {}
with open(fasta_path) as f:
    for line in f:
        if line.startswith(">"):
            seq_id = line[1:].strip().split(" ")[0]
            id_seq_dict[seq_id] = ""
        else:
            sequence = line.strip().replace("U","T")
            id_seq_dict[seq_id] += sequence
~~~
- 
# Research Assistant Agent Skill

> AI-powered academic research and paper analysis assistant

## 功能

- **论文搜索** - arXiv、PubMed、Google Scholar集成
- **论文摘要** - 自动生成论文核心观点摘要
- **文献综述** - 多篇论文对比分析
- **引用管理** - BibTeX/APA/MLA格式引用
- **研究趋势分析** - 领域热点、引用网络

## 使用场景

```
用户: 帮我找一下大语言模型的最新研究进展
Agent: [调用research-assistant skill搜索arXiv，整理最新论文摘要]
```

## 工具函数

### `search_papers(query, sources=['arxiv'], limit=10)`

搜索学术论文。

**参数:**
- `query` (str): 搜索关键词
- `sources` (list): 数据源 ['arxiv', 'pubmed', 'scholar']
- `limit` (int): 返回数量

**返回:**
```python
{
    "papers": [
        {
            "title": "Attention Is All You Need",
            "authors": ["Vaswani, A.", "Shazeer, N."],
            "year": 2017,
            "abstract": "The dominant sequence transduction models...",
            "url": "https://arxiv.org/abs/1706.03762",
            "citations": 50000
        }
    ],
    "total": 1250
}
```

### `summarize_paper(paper_url)`

生成论文摘要。

### `compare_papers(paper_urls)`

多篇论文对比分析。

### `generate_citation(paper, format='bibtex')`

生成引用格式。

### `analyze_trends(field, years=5)`

分析研究趋势。

## 配置

```json
{
    "api_keys": {
        "arxiv": null,
        "pubmed": null,
        "semantic_scholar": "optional"
    },
    "cache_ttl": 86400,
    "default_language": "en"
}
```

## 示例

```python
# 搜索论文
papers = search_papers('large language model', ['arxiv'], 5)
for p in papers['papers']:
    print(f"{p['title']} ({p['year']})")

# 生成引用
citation = generate_citation(papers['papers'][0], 'bibtex')
```

## 安装

```bash
clawhub install SKY-lv/research-assistant
```

## License

MIT

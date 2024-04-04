# DiaSumFact
This repositry contains dataset and code for the ACL2023 paper: [Annotating and Detecting Fine-grained Factual Errors for Dialogue
Summarization](https://aclanthology.org/2023.acl-long.377.pdf)

## Dataset
We provide fine-grained annotations regarding factual errors in dialogue summarization. The data are sampled from [SAMSum](https://aclanthology.org/D19-5409/) and [QMSum](https://aclanthology.org/2021.naacl-main.472/).
Our dataset contains 1340 sentence-level annotations (dialogue-sentence pairs).

### data format
All annotations are in `annotations.json`. Each record is corresponding to a dialogue in the following format.
```
{
    '<dialog-id>': {
        'utterances': [
            '<utt1>',
            '<utt2>',
            ...
        ]
        'query': '<query>'  # empty for records in SAMSum
        'target_summary': '<original reference summary>',
        'dataset_name': '<dataset name>'  # 'QMSum' or 'SAMSum'
        'group_idx': integer in [1,2,3,4,5,6],
        'annotations': {
            '<summarization_model_name>': {
                'model_prediction': model-generated summary, usually containing multiple sentences
                'sentence_annotations': [
                    {
                        'index': integer starting from 0,
                        'sentence': one sentence from the model-generated summary,
                        'annotation': [
                            'error_class': str, the semantic class of the factual error,
                            'error_span': str, the span that contains a factual error,
                            'intrinsic/extrinsic': "intrinsic" / "extrinsic" / "n/a",
                            'comment': explains why there is an error, or a potential correction to the error
                        ]
                    },
                    ...  # other sentences
                ]
            },
            ... # other summarization models
        }    
    }
}
```

## Code
coming soon

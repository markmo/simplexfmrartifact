# simplexfmrartifact

BentoML artifact framework for simpletransformers.

Installation:

    pip install simplexfmrartifact

Usage example (decorate service):

    from simplexfmrartifact.simpletransformers import SimpleTransformersModelArtifact

    @artifacts([SimpleTransformersModelArtifact('tm_train3_roberta_l_weigh')])
    class MyBentoService(BentoService):


Usage example (package model):

    svc = MyBentoService()

    opts = {
        'classpackage': 'simpletransformers.classification',
        'classname': 'MultiLabelClassificationModel',
        'num_labels': 33,
        'args': {
            'use_multiprocessing': False,
            'silent': True
        }
    }

    svc.pack(model_path, opts)

Alternatively, during training:

    svc.pack({'model': my_trained_model, 'model_opts': opts})

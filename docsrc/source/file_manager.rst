.. _file_manager:

File Manager
*************************************

The ``FileManager`` is a ``Component`` that handles file and folder paths.

Given the cinnamon recommended `Code Organization <https://federicoruggeri.github.io/cinnamon_core/dependencies.html>`_, a ``Component`` that allows quick file retrieval and management in the project comes at hand.
This ``Component is the ``FileManager``.

The ``FileManager`` receives a filepath and updates it according to its initialized ``base_directory``.

.. code-block:: python

    my_folder = 'my_folder'
    my_folder = file_manager.run(filepath=my_folder)
    print(my_folder)        # path/to/base_directory/my_folder/


The ``FileManager`` uses the ``FileManagerConfig`` as the default configuration template:

.. code-block:: python

    class FileManagerConfig(Configuration):

        @classmethod
        def get_default(
                cls
        ):
            config = super().get_default()

            # Directories
            config.add(name='logging_directory',
                       value='logging',
                       type_hint=str,
                       tags={'directory'},
                       description="directory name for library logger")

            config.add(name='dataset_directory',
                       type_hint=str,
                       value='datasets',
                       tags={'directory'},
                       description="directory name for storing datasets")

            config.add(name='registrations_directory',
                       type_hint=str,
                       value='registrations',
                       tags={'directory'},
                       description="directory name for storing components and configurations registrations")

            config.add(name='calibrations_directory',
                       type_hint=str,
                       value='calibrations',
                       tags={'directory'},
                       description="directory name for storing calibrated configurations")

            config.add(name='calibration_runs_directory',
                       type_hint=str,
                       value='calibration_runs',
                       tags={'directory'},
                       description="directory name for storing calibration tasks")

            config.add(name='routine_data_directory',
                       type_hint=str,
                       value='routine_data',
                       tags={'directory'},
                       description="directory name where pre-computed routine data "
                                   "(e.g., pre-built cv folds) is stored")

            config.add(name='runs_directory',
                       type_hint=str,
                       value='runs',
                       tags={'directory'},
                       description="directory name where Component results are stored")

            # Filenames
            config.add(name='logging_filename',
                       type_hint=str,
                       value='daily_log.log',
                       tags={'filename'},
                       description="filename for logging")

            config.add(name='calibration_results_filename',
                       type_hint=str,
                       tags={'filename'},
                       value='calibration_results.json',
                       description="filename of summary file storing calibrated model configurations.")

            config.add(name='run_tracker_filename',
                       type_hint=str,
                       tags={'filename'},
                       value='runs_info.csv',
                       description="filename of summary file storing mapping between "
                                   "run folders and registration keys.")

            return config


***************************
Registered configurations
***************************

The ``cinnamon-generic`` package provides the following registered configurations:

- ``name='file_manager', tags={'default'}, namespace='generic'``: the default ``FileManager``.
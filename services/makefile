tox:
	tox;

collect:
	@./db/initialize || $(MAKE) fail
	@./collector/collect_pr_workitem_mapping_details || $(MAKE) fail
	@./collector/collect_workitem_details || $(MAKE) fail
	@./collector/collect_pr_details || $(MAKE) fail
	@./collector/construct_pr_change_details || $(MAKE) fail

db-initialize: tox
	@./db/initialize || $(MAKE) fail

collect-pr-workitem-mapping-details: tox
	@./collector/collect_pr_workitem_mapping_details || $(MAKE) fail

collect-workitem-details: tox
	@./collector/collect_workitem_details || $(MAKE) fail

collect-pr-details: tox
	@./collector/collect_pr_details || $(MAKE) fail

construct-pr-changes: tox
	@./collector/construct_pr_change_details || $(MAKE) fail

fail:
	@python3 handle_failure.py
	@exit 1

# Print help message
help:
	@echo "Usage:"
	@echo "  make collect       - collect all PR informations"

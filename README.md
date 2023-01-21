
1. Найдите, где перечислены все доступные resource и data_source, приложите ссылку на эти строки в коде на гитхабе:

ResourcesMap: map[string]*schema.Resource

<https://github.com/hashicorp/terraform-provider-aws/blob/8e4d8a3f3f781b83f96217c2275f541c893fec5a/aws/provider.go#L411>

DataSourcesMap: map[string]*schema.Resource

<https://github.com/hashicorp/terraform-provider-aws/blob/8e4d8a3f3f781b83f96217c2275f541c893fec5a/aws/provider.go#L169>

2. Для создания очереди сообщений SQS используется ресурс aws_sqs_queue у которого есть параметр name.

2.1 С каким другим параметром конфликтует name? Приложите строчку кода, в которой это указано.

ConflictsWith: []string{"name_prefix"}

<https://github.com/hashicorp/terraform-provider-aws/blob/8e4d8a3f3f781b83f96217c2275f541c893fec5a/aws/resource_aws_sqs_queue.go#L56>

2.2 Какая максимальная длина имени?

errors = append(errors, fmt.Errorf("%q cannot be longer than 80 characters", k))

<https://github.com/hashicorp/terraform-provider-aws/blob/8e4d8a3f3f781b83f96217c2275f541c893fec5a/aws/validators.go#L1038>

2.3 Какому регулярному выражению должно подчиняться имя?

if !regexp.MustCompile(`^[0-9A-Za-z-_]+(\.fifo)?$`).MatchString(value)

<https://github.com/hashicorp/terraform-provider-aws/blob/8e4d8a3f3f781b83f96217c2275f541c893fec5a/aws/validators.go#L1041>

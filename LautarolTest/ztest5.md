<properties
    articleid="vpngwpointtositeconn"
    pageTitle="Point-to-Site VPN connectivity issues information"
    description="Сведения о проблемах с VPN-подключением точка — сеть"
    authors="radwiv"
        ms.author="radwiv"
    selfHelpType="problemScopingQuestions"
    supportTopicIds="32591156"
    productPesIds="16094"
    cloudEnvironments="public,fairfax,blackforest,mooncake"
    schemaVersion="1"
/>
# <a name="point-to-site-vpn-connectivity-issues-information"></a>Сведения о проблемах с VPN-подключением "точка — сеть"
---
{
    "resourceRequired": false,
    "title": "Проблемы с подключением \"точка — сеть\"",
    "fileAttachmentHint": "Загрузите свой профиль VPN, чтобы ускорить предоставление поддержки. В целях безопасности измените или удалите данные сертификата клиента.",
    "formElements": [
        {
            "id": "problem_start_time",
            "order": 1,
            "controlType": "datetimepicker",
            "displayLabel": "Когда появилась проблема?",
            "required": true
        },
        {
            "id": "P2S_connectivity_issues",
            "order": 2,
            "controlType": "dropdown",
            "displayLabel": "Выберите проблему, которая у вас возникла.",
            "watermarkText": "Выбрать параметр.",
            "dropdownOptions": [
                {
                    "value": "Connectionnotestablishing",
                    "text": "Подключение не устанавливается или часто отключается"
                },
                {
                    "value": "Notreachingdestination",
                    "text": "Не удалось достичь определенного места назначения"
                },
                {
                    "value": "Packet drops",
                    "text": "Удаление пакетов"
                },
                {
                    "value": "Throughput",
                    "text": "Пропускная способность"
                },
                {
                    "value": "Latency",
                    "text": "Latency"
                },
                {
                    "value": "Other",
                    "text": "Другие"
                }
            ],
            "required": true
        },
        {
            "id": "source_dest_IP_address",
            "order": 3,
            "controlType": "textbox",
            "displayLabel": "Укажите исходный и конечный IP-адреса (IP-адреса локальной и (или) виртуальной сети)",
            "required": false,
            "useAsAdditionalDetails": false
        },
        {
            "id": "problem_description",
            "order": 4,
            "controlType": "multilinetextbox",
            "displayLabel": "Укажите ОС устройства",
            "required": true,
            "useAsAdditionalDetails": true,
            "hints": [
                {
                    "text": "Описание проблемы"
                },
                {
                    "text": "ОС устройства (версия ОС платформы клиента)"
                }
            ]
        },
        {
            "id": "P2S_tunneltype",
            "order": 5,
            "controlType": "dropdown",
            "displayLabel": "Выберите тип туннеля",
            "watermarkText": "Выбрать параметр.",
            "dropdownOptions": [
                {
                    "value": "IKEv2",
                    "text": "IKEv2"
                },
                {
                    "value": "OpenVPN",
                    "text": "OpenVPN"
                },
                {
                    "value": "SSTP",
                    "text": "SSTP"
                },
                {
                    "value": "dont_know_answer",
                    "text": "Другое, затрудняюсь ответить или нет данных"
                }
            ],
            "required": true
        }
    ]
}
---
